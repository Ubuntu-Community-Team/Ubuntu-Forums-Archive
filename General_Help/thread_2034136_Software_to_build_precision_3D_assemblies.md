---
title: "Software to build precision 3D assemblies"
date: 2012-07-27
forum: General Help
---

### Post by petersfreeman on 2012-07-27
I'm looking for a piece (or pieces) of Linux software that I can use to build a 3D assembly.  I want to build standard components, make copies of them and place them precisely positioned and correctly oriented in 3D space.  I don't want to move or nudge them into place using a mouse.  I want to say "take this piece and place it so that a designated point on the piece is positioned at, say 20,34,14 (x,y,z).  Now orient it from the way it now is by rotating it 90 degrees about the z axis, keeping the designated point in the same position"

I have looked at:
[LIST]
[*]LibreCAD (lacks 3D)
[*]QCad (lacks 3D)
[*]Blender (only mouse driven?)
[*]Wings 3D (only mouse driven?)
[/LIST]

I think that what I am after is a 3D version of LibreCAD that allows commands to be scripted.  That way, I can describe all my standard components in a script file and easily duplicate them and change the location or orientation using tools such as LibreCalc.  

Currently, I am describing my basic components in LibreCalc and using matrices to translate and rotate them to arrive at the final x,y,z co-ordinates of all the points.  I need to now insert them into a CAD tool to render and view the components or the final assembly

**Example**

Say I am building a bearing housing that is bolted down with six bolts.  I can model a single bolt; six points for the top of the bolt head, six points for the bottom of the head, a cylinder for the bolt shank.  This makes a single basic component.  Assuming that the center of the bearing housing will be at the origin (0,0,0)  I would produce six copies of my basic bolt and then precisely describe the position of each bolt so that the center of the top of the bolt head would be correctly placed in xyz space.  I don't want to nudge it so it looks like it is in the right place (+/- 1 mm).  I want to position it exactly right.

Besides the software I have mentioned, is there something that can do part or all of what I just described?  Can I do this with the software I mentioned above?

Thanks,

Peter

---

### Post by PhantomTurtle on 2012-07-27
That can be done with blender. For precision you can use the keyboard. To move an object you press "m"(for move) then "z" (you DON'T need to hold down m while you do this and pressing z will select the z axis) then type in a number using the numberpad to move it to a spot. So if I wanted to move my object along the Z axis I would press,
```
m, z, 21
```
(Again these keys do not need to be held down while the others are being pressed)
(This will need to be done one by one for each axis by substituting "z" with "x" or "y".)
It is similar for rotate and scale. Just substitue the m with "r" (for rotate) or "s" for scale and z can be substituted with "x" or "y". Here is the Blender hotkey reference if you want to know more ([http://download.blender.org/documentation/BlenderHotkeyReference.pdf]("http://download.blender.org/documentation/BlenderHotkeyReference.pdf")) or you can post here again and I can try to help you if I can. Hopefully that helps.

---

### Post by petersfreeman on 2012-07-28
Thanks PhantomTurtle,  I'll look again at Blender.  I just had a look at a tool called Sweet Home 3D (in the Ubuntu repositories).  It is really just for house design layouts, but I can kind of make it work by using just the box and cylinder objects to make my components.  The problem is that although I can rotate an object about the Z axis, I cannot rotate it about other axis.

---

### Post by petersfreeman on 2012-07-28
Can I get Blender to output into .DXF file format, either directly or indirectly through another tool?

---

### Post by PhantomTurtle on 2012-07-29
> **petersfreeman said:**
> Can I get Blender to output into .DXF file format, either directly or indirectly through another tool?

Here is a script for exporting it to .dxf - [http://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/Import-Export/DXF_Importer]("http://wiki.blender.org/index.php/Extensions:2.6/Py/Scripts/Import-Export/DXF_Importer").

---

### Post by petersfreeman on 2012-07-29
Thanks PhantomTurtle, I have been reviewing a number of YouTube videos on Blender uploaded by cgboorman and they are quite helpful.  I've printed off the PDF of the blender hotkeys.

I found this set of videos which is exactly what I am trying to do which is create a 3D house from design.

[https://vimeo.com/785249]("https://vimeo.com/785249")

I'll marked this solved.

Thanks,

---

### Post by PhantomTurtle on 2012-07-29
No problem, I should warn you though that the house tutorial is a bit old(4 years old). It has the old interface. The new interface looks a lot different and you might get confused. Good Luck with your project.

---

