---
title: "[how to] fast monitor switching"
date: 2011-01-05
forum: General Help
---

### Post by jmadero on 2011-01-05
This how to explains how to emulate the Windows Vista/7 &#8220;fast monitor switching&#8221; from the desktop using right click. An image below shows the current look of mine:

[IMG]http://lh6.ggpht.com/_brcrot_nSx4/TSKoAj8lg_I/AAAAAAAABCg/V8JkacQYa-g/Monitors.jpg[/IMG]

How To:

1. Get Nautilus Actions Configuration:

```
sudo apt-get install nautilus-actions
```

2. Find out what outputs you have and what resolutions they support by running the following command in terminal:

xrandr

	You'll get something like this:



```

Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192

VGA1 disconnected (normal left inverted right x axis y axis)

LVDS1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 367mm x 229mm

   1440x900       60.1*+   59.9  

   1360x768       59.8     60.0  

   1152x864       60.0  

   1024x768       60.0  

   800x600        60.3     56.2  

   640x480        59.9  

HDMI1 disconnected (normal left inverted right x axis y axis)

DP1 disconnected (normal left inverted right x axis y axis)

DP2 disconnected (normal left inverted right x axis y axis)
	

```

	I primarily use LVDS1 (my laptop monitor), HDMI1 to my TV and VGA1 to my external monitor so those are the ones I focus on.

3. Create bash files for the configurations that you want. Here are two examples of mine (two different files):

```

	CODE

	DUALSCREEN TO EXTERNAL

	#!/bin/bash



	xrandr --output VGA1 --pos 100x0 &&



	xrandr --output LVDS1 --pos 1680x150;
	TO TV ONLY

	#!/bin/bash



	xrandr --output HDMI1 --auto;

	xrandr --output LVDS1 &#8211;off;


```

The first one I did absolute positioning because I didn't like the way that the auto positioning was happening. In order to get it working right I just played around with placements in terminal running commands like this:

```
xrandr --output VGA1 --pos 100x0 && 
```
	
I got the first screen where I wanted it and then put the second one in relation to the first. If you want to have a visual of where screens are as you play around with the numbers just open up the monitors GUI within system &#8594; preferences, the screens will move around as you adjust the numbers in the terminal


Make as many separate bash files as you want, I'm working on 5 now:

> 
	TV ON, LAPTOP OFF
	TV ON, LAPTOP ON
	EXTERNAL ON, LAPTOP OFF
	EXTERNAL ON, LAPTOP ON
	LAPTOP ON



Save these as separate files with, I use sh extension. 

4. Combine the bash files with Nautilus Configurations

	Go to system &#8594; preferences &#8594; nautilus actions configuration

	Go to File &#8594; New Menu

	In context label make it whatever you want, mine in the example is Monitor &#8211; Output

	Then go to  File &#8594; New Action

	Here is where you'll make the physical action, in the first section listed &#8220;Action&#8221; in the tab, list your Context Label (Example, TV Only), and make sure to check &#8220;Display item in location context menu&#8221;

	Go to the command tab, browse to the path of your file corresponding to that action and select the file. Scroll to the beginning of the path and put &#8220;bash&#8221; (no  quotes) before the path:


> bash /home/joel/Documents/Computer/Scripts/HDMIOnly.sh


5. On the left panel of the screen, select your action and drag it into the Menu that you created. See image below:

[IMG]http://lh3.ggpht.com/_brcrot_nSx4/TSTEcjLkPrI/AAAAAAAABCk/b1hyosdl3P8/s576/imageII.jpg[/IMG]


That's it, repeat the proces for other actions. If you want icons then follow the next steps:



6. Select the action that you want to add an icon to, on the &#8220;Action&#8221; tab half way down it lists &#8220;Icon&#8221;, browse to the icon of your choice and select it

7. To have the icons appear you have to enable them in gconf-editor

	terminal
	gconf-editor

	Desktop &#8594; Gnome &#8594; Interface, check &#8220;menus have icons&#8221;


EXTERNAL LINKS OF INTEREST:

xrandr config: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")

Nautilus Actions: [http://www.foogazi.com/2007/11/05/adding-shortcuts-to-the-right-click-menu-in-ubuntu/]("http://www.foogazi.com/2007/11/05/adding-shortcuts-to-the-right-click-menu-in-ubuntu/")

---

