
https://unpkg.com/aframe-environment-component@1.1.0/dist/aframe-environment-component.min.js



aframe-environment-component”


we can attach the environment component to the scene using <a-entity> tag.
This will set up the default environment properties.
  
  
  
  There are many properties which are available that we can set for the environment component. We will be learning to use a few of the properties associated with this component to override the default setting, like-
  
  
  preset- This is used to set the environment type and valid values are none, default, contact, egypt, checkerboard, forest, goaland, yavapai, goldmine, threetowers, poison, arches, tron, japan, dream, volcano, starry, osiris.
  
  
  skyType-This is used to set the type of sky element and valid values are color, gradient, atmosphere.
  
skyColor- This can be used to set the color of the sky element when the skyType is set color or gradient.
  
lighting- This is used to set up the lighting in the environment and the valid values are none, distant, point.
*********************************
  
  
  Let’s make this scene a very basic military shooting scene.
For this we can add a few more elements by ourselves by adding models in the scene.
Since we will make a military shooting scene, we can use some enemy tanks, a few boxes that might be lying around in the scene and some wire-fences.
  
  
  To start with, I will be adding some wire-fences. We will use wire-fence 3D models and write a component to add fences in all four directions.
  *******************************************************
  
  
  
  gameObjects.js file
  
  
  
  "wire-fence” component is created to add wire-fence as a boundary on all the side in the game environment
  
  We want to create a boundary fence from left to right at a far away distance from the camera into the screen.
We can add “for loop” to create 10 entities from left to right in the .init() method.
  
  
  Note: Adding so many gLTF models will make the scene very heavy to load based on the system compatibility. If the system is taking a lot of time to load the scene, reduce the number of models on each side to load the scene by reducing the loop counter to 5 or any other number
  
  
  We can start with x position -20 and keep on increasing it by 5 till the end of the loop, keeping y and z position fixed.
Now, we can create the entity using document.querySelector() in the loop.
  
  And set the attribute- ● id
● position
● scale
● gltf-model
  ● static-body
  
using setAttribute().
Then we can append the child to the
scene element.
  
  
 create an  <a-entity> tag and attach a “wire-fence” component in the index.html file and then test the output.
    
  Let's have three more variables for creating a fence boundary on the other three sides.
  
  
  Now we can repeat steps to set the attributes of these wire fences also.
For the fences on the left and right side, we will need to increase the z position and keep x and y fixed going from front to back direction.
Take a variable at top for z position.
Decrease the z position till the end of the loop.
  
  
  Set the gLTF model attribute for each fence.
  
  
  Set the rotation of two wire-fences to 90 degrees on y axis to make them vertical.
  
  Set the static-body attribute and append the entities to the scene element.
  
  *********************************
  Now let’s add shooting sounds. Every time the player shoots the bullet, the shot sound must be played.

  use A-Frame <audio> in asset management, <a-assets>.
In <audio>, we can give the id to the audio asset and set the src of the sound.
  
  Now let’s create an entity to set the sound component properties.
src- The id source of the sound set in the <audio> asset.
poolSize- Number of times the sound can be played simultaneously.
autoplay- Whether to play sound automatically or not.
volume- volume of the sound.
  
  loop-Whether to repeat the sound infinitely.
  
  
  
  To play the sound, we can write a function, shootSound().
<The teacher writes a function in the shoot.js file in the “bullets” component.>
● Select the entity using document.querySelector().
● Call playSound() method of the component, entity.components.sound.p laySound().
● Call the shootSound() in the shoot() function.
  
  
  **********************
  
  The boxes component has a schema with height, width and depth of boxes each with default values of 3.
  
  boxes will lie on ground, hence the y position attribute will remain constant. But the x and z position will be random to change the position of the horizontally from left to right and to change the depth
  
  he footStep.mp3 sound file path is added using <audio> in <a-assets>
  
  
    
  
  
  
