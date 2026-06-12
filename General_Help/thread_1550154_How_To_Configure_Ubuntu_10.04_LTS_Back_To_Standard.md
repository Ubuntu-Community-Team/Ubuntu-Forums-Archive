---
title: "How To Configure Ubuntu 10.04 LTS Back To Standard - Tweaks and Tips"
date: 2010-08-10
forum: General Help
---

### Post by TuxIsCute on 2010-08-10
With many people out there unhappy with what has been called Ubuntu's change simply for the sake of change update, many people are running around trying to get things back in line with the common Ubuntu we all knew and loved before.  I have done this and it has taken some time so I figure I should share the fruits of my work with the fine people here on the forums.

This will cover many tweaks and tips and as always there may be faster easier ways (some are even listed on the internet) but this is the only way I could get it to work out for me.

**-Things Covered Herein-**
1.**-Plymouth Boot Screen-**
2.**-The close, minimize, and maximize buttons-**
3.**-Center The Title-**
4.**-Login Screen-**
5.**-Getting Rid of the Icons on the GNOME Menu-**
6.**-Get Rid of the Mail Icon and the IM Icon on the indicator panel thing-**

**-Plymouth Boot Screen-**

When you first boot up Ubuntu 10.04 LTS you're greeted with the purple Ubuntu screen with small white dots turning red to show the booting process.  When I saw this, I thought, “This has got to change.”  So this is what I will show you first.

You're going to need to get rid of the plume color.  So fire up terminal and type in this following command to open gedit as root so you can edit the given file.
```
sudo gedit /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script
```
Then scroll down until you see these lines:
```
Window.SetBackgroundTopColor (0.16, 0.00, 0.12); # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.16, 0.00, 0.12); # an equally nice colour on the bottom
```
This holds the ugly plume color.  You going to need to edit it down.  To do this, you take the RGB values of your new color and then divide that by 255 to give you the point value above.  (IE: 40,0,30 is plume purple.  To get the values above you divide those numbers by 255.  40/255=0.16,0/255=0,30/256=0.12)  To be easy, I'll change it to black.  That is simply 0.00,0.00,0.00.  So edit the values like so:
```
Window.SetBackgroundTopColor (0.00, 0.00, 0.00); # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.00, 0.00, 0.00); # an equally nice colour on the bottom
```
Save and exit gedit.

In terminal run the following command:
```
sudo update-initramfs -c -k `uname -r`
```
If you rebooted now you'd see a black screen with purple outlined images.  That sucks.

So now, you need to edit the actual images.  They have a nice cozy place where they live.  So run the following command in terminal to open nautilus as root:
```
sudo nautilus
```
Navigate to the following address:
```
/lib/plymouth/themes/ubuntu-logo
```
There are several files we'll need to edit in this folder.

1.password_field16.png
2.progress_dot_off.png
3.progress_dot_off16.png
4.progress_dot_on.png
5.progress_dot_on16.png
6.ubuntu_logo.png
7.ubuntu_logo16.png

In nautilus copy them somewhere else and open each one in GIMP.  You're going to do the same thing to all of them.  In GIMP, click on the layer to highlight it and then right-click the layer and select “Add Alpha Channel.”  Then use the select option to select “By Color” and select the ugly purple color and press the delete key.  This will make all of the purple areas transparent.  Do this for all of the images.  Copy them pack into the other folder.  If you don't want to overwrite the original files, you can rename them to “.old” extension.

Now no matter what color you edit the above .script code to, the images will reflect it because the bits that matter are transparent.

Reboot to see the awesome blackness instead of the awful purpleness.  (You can also edit the colors of the images, duh.)

**-The close, minimize, and maximize buttons-**

There is two ways to go about doing this.  The first is easy.  The second is still easy too.

1.Use Ubuntu Tweak.  This is fast and simple.  Move the buttons to where you want them.  Show or hide the buttons you don't care about.
2.Use gconf-editor to edit the button_layout key at apps->metacity->general to :minimize,maximize,close.  [The colon (:) is important.  Don't leave it out.]

**-Center The Title-**

This wasn't the easiest thing in the world to do and you have to do it for your specific theme.  You do it by editing a specific xml file in your themes folder.

In terminal we will call the following:
```
sudo gedit /usr/share/themes/Radiance/metacity-1/metacity-theme-1.xml

```
This is for the **Radiance** theme only.  If you want to edit **Ambiance** be sure to put that in this line and you will have to edit the below text a little so the you are moving the right bits around.   I only did it for Radiance.  When you have that open you'll see an area that begins:
```
<!-- Window Title -->.
```

Make it look like this (IE: copy and paste):
```
<!-- Window Title -->



<draw_ops name="draw_title_text_normal">

<title color="#333"

x="(width-title_width)/2"

y="(((height - title_height) / 2) `max` 0)+1"/>

<!-- <title color="#333"

x="10"

y="(((height - title_height) / 2) `max` 0)-1"/>

<title color="#333"

x="9"

y="(((height - title_height) / 2) `max` 0)"/>

<title color="#333"

x="11"

y="(((height - title_height) / 2) `max` 0)"/>

<title color="#dfd8c8"

x="10"

y="(((height - title_height) / 2) `max` 0)"/> -->



</draw_ops>



<draw_ops name="draw_title_text_inactive">

<title color="#333333"

x="(width-title_width)/2"

y="(((height - title_height) / 2) `max` 0)+1"/>

<!-- <title color="#333333"

x="10"

y="(((height - title_height) / 2) `max` 0)-1"/>

<title color="#333333"

x="9"

y="(((height - title_height) / 2) `max` 0)"/>

<title color="#333333"

x="11"

y="(((height - title_height) / 2) `max` 0)"/>

<title color="#99958b"

x="10"

y="(((height - title_height) / 2) `max` 0)"/> -->

</draw_ops>
```

This will center the title text on the title bar.  Save that file and exit gedit.
You will need to log out and back in to see the changes.

**-Login Screen-**

The image behind the login can easily be changed.  Again there are two ways to go about doing this.

1.Ubuntu Tweak.  Easy as pie!
2.Is a bit more difficult.

For the second option, run this command in terminal:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

```
The log out and back in.  This will bring up an appearance window.  Here change the background image of the login screen.  Yey.  Done.  (This is supposed to also allow you to change the plymouth background color but I never got it to work.)

When you get back in run the following command in terminal so that the appearance window does come up all the time:
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop



```

Also, in Ubuntu Teak there is an option to make it so that people logging into th computer has to type both the username and password.  There doesn't seem to be any other way to get this functionality.

**-Getting Rid of the Icons on the GNOME Menu-**

Still honestly doing this one.  I've been able to get rid the main ones but the ones on the sub-menu remain.

Still to get rid of them go to the folders that hold them in root nautilus.  They can be found at
```
/usr/share/icons
```.  Basically ANY sub-folder named “category” should be renamed to something else... anything else!  Do not delete them (for obvious reasons)!

You then need to hunt down Wine.png and the icon for the Ubuntu Software Center.  I haven't found the latter and the former can be in a number of places so that is not advantageous to list them all here.  Rename those files to like wine.png.bak and there you go.   You have to reboot to see the changes.  There are places that hold the sub-menu items and those can be edited the same way.  I just haven't done so.

**-Get Rid of the Mail Icon and the IM Icon on the indicator panel thing-**

Run the following in terminal:
```
sudo apt-get remove indicator-me indicator-messages

```

Well, there you have it.  Some great tips to make it all work like it should.  One thing is that sometimes when you restart there is no window boarders at all.  This is known to happen.  The command that fixed it for me was:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
But then again, I have an NVIDIA graphics card.  If you don't, you'll need to find your own solution.

I hope this has been somewhat helpful to you guys out there.  I also hope that in putting it in one place, it might stop some people out there from searching for hours for something that is simple.

ALSO,  I really do recommend the great program Ubuntu Tweak.  While it isn't supported by Ubuntu, it makes sure that Ubuntu lives up to its potential.  Check them out at: ```
http://www.ubuntu-tweak.com/
```  I actually wish Ubuntu would support these guys.

I hope this is the right place.  If not, will you please move it for me.

---

### Post by chaanakya_chiraag on 2010-08-24
I just completely disabled Plymouth, as it seemed to freeze the boot because of the proprietary nvidia driver. Also, I echo everything into tty2, so I just have a blinking cursor and nothing else. Very spartan, very clean, one flicker :)

---

### Post by chaanakya_chiraag on 2010-08-24
Btw, do you know if there are any ill effects to completely disabling Plymouth?  That is, Plymouth doesn't even start at all on my computer.

---

### Post by rykel on 2010-08-25
Wow, thank you! While I am not trying to change my Ubuntu Lucid back to the good old days settings yet, this should come in useful at one point. You have put in a lot of effort on this and I commend you! Regards.

---

