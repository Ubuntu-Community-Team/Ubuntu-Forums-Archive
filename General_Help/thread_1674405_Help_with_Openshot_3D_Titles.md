---
title: "Help with Openshot 3D Titles"
date: 2011-01-23
forum: General Help
---

### Post by sudoer541 on 2011-01-23
I am trying to use the 3D titles using Openshot, and I get the following message when I try to preview and apply them:


```
Blender, the free open source 3D content creation suite is required for this action (http://www.blender.org).

Please check the preferences in OpenShot and be sure the Blender executable is correct.  This setting should be the path of the 'blender' executable on your computer.  Also, please be sure that it is pointing to Blender version 2.5 or greater.

Blender Path:
blender

Error Output:
No frame was found in the output from Blender

```

I have Blender ```
version 2.56.0 Beta r34468.
``` I checked the path for the Blender executable, and I get: ```
 blender
``` Does anyone know how to solve this?

---

### Post by sudoer541 on 2011-01-24
Anyone? 0_o

---

### Post by arron on 2011-02-02
I had this problem too, this is how i fixed it:

Install a current openshot, the repositories are a bit behind, so i used this PPA:
```

#current openshot
sudo add-apt-repository ppa:jonoomph/openshot-edge
sudo apt-get update
sudo apt-get install openshot openshot-doc

```


Now you need a current blender, you can use this PPA, or you can manually download it from thier site, and point the blender link in openshot options to where you downloaded it from.  I like this PPA to keep up to date.
```

#current blender
sudo add-apt-repository ppa:cheleb/blender-svn
sudo apt-get update
sudo apt-get install blender

```

Both of these PPA's are listed on the openshot and blender websites, I have nothing to do with them.

Now here is the trickiest part.....
Run this command to edit some config files, one gedit window will open with several .xml files open:
```

sudo gedit /usr/lib64/pymodules/python2.6/openshot/blender/*.xml

```
*edit - you may need to substitute 32 for a 32bit os, im not sure.

Now in gedit hit "Control-H", this will pop up a replace dialog.

Search for "CENTRAL"
Replace with "CENTER"

Go threw and replace each CENTRAL with CENTER for each file, i believe most had CENTRAL 3 times.  Replace all of them in each file, then save and close them.

And bingo, you should be up and running.

I believe there is a fix for this on the way, it has been listed as a bug in openshot with a new blender version.

Should be up and running with 3d text.  I want to learn some blender tools now to make my own.



*credit* I got the info from here on how to fix it, i cant take all the credit. I just made a simple howto to fix it

[http://openshotusers.com/forum/viewtopic.php?f=12&t=720](http://openshotusers.com/forum/viewtopic.php?f=12&t=720)

---

### Post by cptNightrain on 2011-02-03
Thanks for the fix - works great! For those using 32bit Ubuntu, the xml files are in a different location so use the following code instead of what's posted above:
```
sudo gedit /usr/lib/pymodules/python2.6/openshot/blender/*.xml
```

---

### Post by Braveheart1980 on 2011-02-06
Well I just did that, but it still says CENTRAL in openshot , although the xml's say CENTER.....

Here's the error I am getting

```
Traceback (most recent call last):
  File "/home/george/.openshot/blender/cfbeeccc-323a-11e0-abe4-0013e834a47d/glare.py", line 104, in <module>
    text_object.align = params["spacemode"]
TypeError: bpy_struct: item.attr = val: enum "CENTRAL" not found in ('LEFT', 'CENTER', 'RIGHT', 'JUSTIFY', 'FLUSH')
No frame was found in the output from Blender
Blender render thread finished

```

And of course glare.py doesnt even have CENTRAL:

```
#	OpenShot Video Editor is a program that creates, modifies, and edits video files.
#   Copyright (C) 2009  Jonathan Thomas
#
#	This file is part of OpenShot Video Editor (http://launchpad.net/openshot/).
#
#	OpenShot Video Editor is free software: you can redistribute it and/or modify
#	it under the terms of the GNU General Public License as published by
#	the Free Software Foundation, either version 3 of the License, or
#	(at your option) any later version.
#
#	OpenShot Video Editor is distributed in the hope that it will be useful,
#	but WITHOUT ANY WARRANTY; without even the implied warranty of
#	MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#	GNU General Public License for more details.
#
#	You should have received a copy of the GNU General Public License
#	along with OpenShot Video Editor.  If not, see <http://www.gnu.org/licenses/>.


# Import Blender's python API.  This only works when the script is being
# run from the context of Blender.  Blender contains it's own version of Python
# with this library pre-installed.
import bpy

# Debug Info:
# ./blender -b test.blend -P demo.py
# -b = background mode
# -P = run a Python script within the context of the project file

# Init all of the variables needed by this script.  Because Blender executes
# this script, OpenShot will inject a dictionary of the required parameters
# before this script is executed.
params = {		
			'title' : 'Oh Yeah! OpenShot!',
			'extrude' : 0.1,
			'bevel_depth' : 0.02,
			'spacemode' : 'CENTER',
			'text_size' : 1.5,
			'width' : 1.0,
			'fontname' : 'Bfont',
			
			'color' : [0.8,0.8,0.8],
			'alpha' : 1.0,
			
			'output_path' : '/tmp/',
			'fps' : 24,
			'quality' : 90,
			'file_format' : 'PNG',
			'color_mode' : 'RGBA',
			'horizon_color' : [0.57, 0.57, 0.57],
			'resolution_x' : 1920,
			'resolution_y' : 1080,
			'resolution_percentage' : 100,
			'start_frame' : 20,
			'end_frame' : 25,
			'animation' : True,
		}


#BEGIN INJECTING PARAMS
params['specular_color'] = [1.0, 1.0, 1.0]
params['start_frame'] = 1
params['spacemode'] = 'CENTER'
params['title'] = 'My Title'
params['file_name'] = 'TitleFileName'
params['use_alpha'] = 'Yes'
params['diffuse_color'] = [1.0, 1.0, 1.0]
params['end_frame'] = 250
params['extrude'] = 0.1
params['bevel_depth'] = 0.02
params['text_size'] = 1.0
params['width'] = 1.0
params['resolution_y'] = 576
params['resolution_x'] = 720
params['file_format'] = 'PNG'
params['resolution_percentage'] = 100
params['color_mode'] = 'RGB'
params['output_path'] = '/home/george/.openshot/blender/cfbeeccc-323a-11e0-abe4-0013e834a47d/TitleFileName'
params['fps'] = 25
params['quality'] = 100
params['animation'] = True
#END INJECTING PARAMS


#ONLY RENDER 1 FRAME FOR PREVIEW
params['start_frame'] = 125
params['end_frame'] = 125


#END ONLY RENDER 1 FRAME FOR PREVIEW


# The remainder of this script will modify the current Blender .blend project
# file, and adjust the settings.  The .blend file is specified in the XML file
# that defines this template in OpenShot.
#----------------------------------------------------------------------------

# Modify Text / Curve settings
#print (bpy.data.curves.keys())
text_object = bpy.data.curves["Text"]
text_object.extrude = params["extrude"]
text_object.bevel_depth = params["bevel_depth"]
text_object.body = params["title"]
text_object.align = params["spacemode"]
text_object.size = params["text_size"]
text_object.space_character = params["width"]

# Get vector font object (these are defined in the .blend file)
# Only fonts added to your .blend file can be used here
font = bpy.data.fonts[params["fontname"]]
text_object.font = font

# Change the material settings (color, alpha, etc...)
material_object = bpy.data.materials["Material.001"]
material_object.diffuse_color = params["diffuse_color"]
material_object.specular_color = params["specular_color"]
material_object.alpha = params["alpha"]

# Set the render options.  It is important that these are set
# to the same values as the current OpenShot project.  These
# params are automatically set by OpenShot
bpy.context.scene.render.filepath = params["output_path"]
bpy.context.scene.render.fps = params["fps"]
#bpy.context.scene.render.quality = params["quality"]
bpy.context.scene.render.file_format = params["file_format"]
if params["use_alpha"] == "No":
	bpy.context.scene.render.color_mode = "RGB"
else:
	bpy.context.scene.render.color_mode = params["color_mode"]
#bpy.data.worlds[0].horizon_color = params["horizon_color"]
bpy.context.scene.render.resolution_x = params["resolution_x"]
bpy.context.scene.render.resolution_y = params["resolution_y"]
bpy.context.scene.render.resolution_percentage = params["resolution_percentage"]
bpy.context.scene.frame_start = params["start_frame"]
bpy.context.scene.frame_end = params["end_frame"]

# Render the current animation to the params["output_path"] folder
bpy.ops.render.render(animation=params["animation"])

```

glare.xml , doesn't have CENTRAL either :

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE openshot-effect>
<effect>
	<title translatable="True">Glare</title>
	<description translatable="True">Glare</description>
	<icon>glare.png</icon>
	<category>Video</category>
	<service>glare.blend</service>
	
	<param name="file_name" type="text" title="File Name" description="">
		<default>TitleFileName</default>
	</param>
	
	<param name="title" type="text" title="Title" description="">
		<default>My Title</default>
	</param>
	
	<param name="extrude" type="spinner" title="Extrude" description="">
		<min>0.0</min>
		<max>1.0</max>
		<default>0.1</default>
	</param>

	<param name="bevel_depth" type="spinner" title="Bevel Depth" description="">
		<min>0.0</min>
		<max>1.0</max>
		<default>0.02</default>
	</param>
	
	<param name="spacemode" type="dropdown" title="Text Alignment" description="">
		<values>
			<value name="CENTER" num="CENTER"/>
			<value name="LEFT" num="LEFT"/>
			<value name="RIGHT" num="RIGHT"/>
		</values>
		<default>CENTER</default>
	</param>
	
	<param name="text_size" type="spinner" title="Text Size" description="">
		<min>0.0</min>
		<max>10.0</max>
		<default>1.0</default>
	</param>
	
	<param name="width" type="spinner" title="Text Width" description="">
		<min>0.0</min>
		<max>10.0</max>
		<default>1.0</default>
	</param>

	<param name="diffuse_color" type="color" title="Diffuse Color" description="">
		<default>#ffffff</default>
	</param>
	
	<param name="specular_color" type="color" title="Specular Color" description="">
		<default>#ffffff</default>
	</param>
	
	<param name="use_alpha" type="dropdown" title="Use Alpha" description="">
		<values>
			<value name="Yes" num="Yes"/>
			<value name="No" num="No"/>
		</values>
		<default>Yes</default>
	</param>

	<param name="start_frame" type="spinner" title="Start Frame" description="">
		<min>1</min>
		<max>1</max>
		<default>1</default>
	</param>
	
	<param name="end_frame" type="spinner" title="End Frame" description="">
		<min>250</min>
		<max>250</max>
		<default>250</default>
	</param>
</effect>
```

ANy ideas?

---

### Post by styven on 2011-02-13
Same here done all you suggested and get...........


Error Output:
No frame was found in the output from Blender

I have blender installed with launcher etc, it opens up fine on its own.

---

### Post by sudoer541 on 2011-02-14
I just updated openshot to version 1.3.0 and I still have the same problem.
I followed the tutorial above and on the script it says "Center" instead of "central".
I still get the same message as my first post above. 

I have the latest version of Blender and openshot on ubuntu 10.10.

---

### Post by sudoer541 on 2011-02-14
SOLVED!!!!!!!!!!!!!):P:p

ok... so .... here it goes::p

go to EDIT> blender executable and type: "**usr/bin/blender**" and it should work!!!

it works perfectly, however the rendering is too slow :(
Is there anything we can do about that? or is my pc too slow to run openshot? 

It is possible to render 50 frames instead of 900 (or max)?

---

### Post by tostrye on 2011-02-15
Rendering is slow. To be fair, rendering in Winblows is slow too. Unfortunately this is a hardware problem as far as I know. I would like to know if you can decrease the # of frames.

---

### Post by arron on 2011-02-15
I just read on the Openshot FB page that they released 1.3 to the Ubuntu PPA.  This should mean you can upgrade to ver 1.3 with the normal updates.  Can someone confirm this, and if the "CENTER" and blender issue works without any tweets?

Thanks

---

### Post by tm6148 on 2011-02-16
I installed OpenShot 1.3 yesterday and Blender this morning from the PPA's mentioned in this thread and I didn't have to tweak a thing.  This is on Maverick in Virtualbox.

---

### Post by schum3,1415 on 2012-01-07
Hi,

I've been following all the steps given by *arron* but I still keep on getting the above mentioned error message: "No frame was found in the output from Blender", when trying to create a new animated title.

The "CENTRAL"->"CENTER"-issue has already been taken care of in the current blender-version.

The link in OpenShot-Preferences points to the right directory (in my case: /usr/bin/blender)

system details: Lenovo Thinkpad T410 running 64bit Ubuntu 11.04
OpenShot: 1.4.0
Blender: 2.61

using Inkscape in OpenShot works just fine.

Thx in advance for your help!

---

