---
title: "Tablet Buttons don't work (Genius GPEN F610)"
date: 2009-09-08
forum: General Help
---

### Post by tudor117 on 2009-09-08
I have a Genius G-Pen F610 tablet which works great except for the buttons.
I've tried all the tutorials but did nothing to affect the button input.
"lsusb" gives: Bus 002 Device 026: ID 172f:0034 

while "xinput list" gives
```
 $ xinput list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Microsoft Microsoft Wireless Optical Desktop? 2.10"    id=6    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Macintosh mouse button emulation"    id=7    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Microsoft Microsoft Wireless Optical Desktop? 2.10"    id=8    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"WALTOP International Corp. Slim Tablet eraser"    id=2    [XExtensionPointer]
    Num_buttons is 6
    Num_axes is 3
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1680
        Resolution is 1000
    Axis 1 :
        Min_value is 0
        Max_value is 1050
        Resolution is 1000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1000
"WALTOP International Corp. Slim Tablet cursor"    id=3    [XExtensionPointer]
    Num_buttons is 6
    Num_axes is 3
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1680
        Resolution is 1000
    Axis 1 :
        Min_value is 0
        Max_value is 1050
        Resolution is 1000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1000
"WALTOP International Corp. Slim Tablet pad"    id=4    [XExtensionPointer]
    Num_buttons is 6
    Num_axes is 3
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1680
        Resolution is 1000
    Axis 1 :
        Min_value is 0
        Max_value is 1050
        Resolution is 1000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1000
"WALTOP International Corp. Slim Tablet"    id=5    [XExtensionPointer]
    Num_buttons is 6
    Num_axes is 3
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1680
        Resolution is 1000
    Axis 1 :
        Min_value is 0
        Max_value is 1050
        Resolution is 1000
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1000

```"xinput set-button-map "WizardPen Tablet" 1 3 2 " or with 6 numbers following does nothing.
I have Ubuntu Jaunty 64 with 0.7.0-alpha2 driver.

Any help or ideas greatly appreciated.

---

### Post by Favux on 2009-09-08
Hi tudor117,

Did you try the linuxwacom drivers?  I'm asking because xinput is identifying your tablet as a Waltop.  Here's the Waltop section of the 10-wacom.fdi:
```
      <match key="info.product" contains="WALTOP">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
```
I suppose there could be a "conflict" between the wacom.fdi and the wizardpen.fdi with both trying to configure the tablet.

---

### Post by tudor117 on 2009-09-09
OMG OMG OMG THANK YOU!!!
It works now!!
and it's way better than before
the pressure sensitivity is way smoother :D

all I had to do is rename the wizarpen fdi and all's great :D

---

### Post by Favux on 2009-09-09
Hi tudor117,

Good news!  You're welcome.

We may be able to improve things even more if you're interested.  I'm not sure because you may have the first Waltop tablet I've helped setup in Jaunty.  I don't know how heavy you're into graphics and using your tablet.  Check in Synaptic Package Manager that in addition to xserver-xorg-input-wacom you also have wacom-tools installed.  If not go ahead and install it and reboot.

Then to see what I'm talking about enter in a terminal:
```
xsetwacom list
```
It should return linuxwacom names like stylus, eraser, cursor (if you have a tablet mouse), and pad.  If it's blank then you can't use 'wacomcpl' (the linuxwacom calibration and configuration gui) or xsetwacom commands.  To see what HAL is calling your tablet stuff enter in a terminal:
```
xinput --list
```

---

### Post by tudor117 on 2009-09-10
Yea, I am interested in making it better! :D
I was planning on using my tablet in Blender and such.
However, "xsetwacom list" is empty and "xinput --list" shows the following.
```
$ xinput --list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"WALTOP International Corp. Slim Tablet"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 20000
        Resolution is 1016
    Axis 1 :
        Min_value is 0
        Max_value is 12500
        Resolution is 1016
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"WALTOP International Corp. Slim Tablet pad"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 6
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 20000
        Resolution is 1016
    Axis 1 :
        Min_value is 0
        Max_value is 12500
        Resolution is 1016
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is 0
        Max_value is 0
        Resolution is 1
    Axis 4 :
        Min_value is 0
        Max_value is 0
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"WALTOP International Corp. Slim Tablet cursor"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 6
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 20000
        Resolution is 1016
    Axis 1 :
        Min_value is 0
        Max_value is 12500
        Resolution is 1016
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -900
        Max_value is 899
        Resolution is 1
    Axis 4 :
        Min_value is -1023
        Max_value is 1023
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"WALTOP International Corp. Slim Tablet eraser"    id=5    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 20000
        Resolution is 1016
    Axis 1 :
        Min_value is 0
        Max_value is 12500
        Resolution is 1016
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Microsoft Microsoft Wireless Optical Desktop? 2.10"    id=6    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Macintosh mouse button emulation"    id=7    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Microsoft Microsoft Wireless Optical Desktop? 2.10"    id=8    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255

```I got so excited that I was going to use a gui that I didnt read about the "if it's empty it wont work". I got kinda confused :P

Either way, my tablet doesn't have an eraser it's only the pen, with 2 buttons on it.
I can configure them using
```
xinput set-button-map "WALTOP International Corp. Slim Tablet" 1 2 
```However the second value changes both buttons simultaneously and it's really hard to work like that (so that they're both the same thing). In blender it's either no select/deselct/cancel_move or no rotating view using tablet....
Is there anything I can do?

Thanks again for all your help :D

---

### Post by Favux on 2009-09-10
Hi tudor117,

OK, the blank xsetwacom (you did install wacom-tools?) and the xinput are what I expected.

But first is your tablet USB?  Does it plug into a usb port?

---

### Post by tudor117 on 2009-09-10
Yea, it's a USB tablet and I installed the wacom-tools from the repos.

---

### Post by Favux on 2009-09-10
Hi tudor117,

Good, usb is what we wanted.

Like Blender, wacomcpl has 'stylus' "hardcoded" in.  So we want "xsetwacom list" to return stylus and the rest.  We found a .fdi that does parse the names HAL is returning into linuxwacom names.  Let's see if by using a modified version of it (for Waltop) we can further set up your tablet using linuxwacom.

The .fdi and instructions are in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Don't download the attached .fdi, we need to change it for the Waltop.  We should look at 'lshal' by doing:
```
lshal>lshal.txt
```
Which would give us a text file we could search with find.  For 'Waltop' etc.  We'd be looking for the Waltop section(s) in lshal.  But let's see if we can be lazy and get lucky.  Try the .fdi attached below using the instructions in post #176.

Then see if "xsetwacom list" returns linuxwacom names.

Good luck!

---

### Post by tudor117 on 2009-09-10
Ok first of, thank you so much!
Your fdi works great. It works with the gui and xsetwacom list works great.
Blender now has pressure sensitivity which is even better!

But there's still something wrong with the buttons... Even in the wacomcpl, Button 2 changes both the buttons on my stylus. Is there away to check if the stylus returns the same event on both buttons?

---

### Post by Favux on 2009-09-10
Hi tudor117,

Outstanding!  So we now have a working Waltop .fdi.  Cool.

In wacomcpl when you click on stylus and then tool buttons, are you saying even if you configure Button2 and Button3 differently, they end up doing whatever Button2 is set to?  Button1 is the stylus tip by the way.

I think the only way would be to look at the wacdump output, but I don't think it works in Jaunty.  It could be a problem with linuxwacom handling your stylus buttons or maybe it's just a limitation on your Waltop buttons?

---

### Post by tudor117 on 2009-09-10
> In wacomcpl when you click on stylus and then tool buttons, are you saying even if you configure Button2 and Button3 differently, they end up doing whatever Button2 is set to? Button1 is the stylus tip by the way.Yea, that's exactly it. Button 2 changes both buttons on the pen.

I doubt it's the Waltop buttons themselves because the box states it has 2 working buttons plus the pen tip (I havent tried under windows though). Is it possible to test under an other version of ubuntu/linux? I can try it under a vm.
However, one button is better than none!

---

### Post by Favux on 2009-09-10
Hi tudor117,

Are the stylus buttons two physically seperate buttons or are they actually a rocker switch?  I'm wondering about a hardware problem.  And didn't you say something about trying a button mapping?

---

### Post by antario91 on 2009-09-11
Hey, Guys
I have the same tablet (Favux, your information helped much). I have the same problem with the buttons. There is no hardware problem, the buttons are tho physically separate buttons and it works under Windows (both XP and Vista/Seven).

---

### Post by Favux on 2009-09-11
Hi antario91 and tudor117,

Great antario91.  Two Waltops work with the .fdi!

Very helpful to know it's not the hardware.  So is it just a problem with the Waltop interfacing with the linuxwacom drivers and/or wacomcpl?

Let's see what your button map says.  We know the name but in terminal enter:
```
xinput list | grep 'id='
```
And then from the name you get there enter:
```
xinput get-button-map "name"
```
And let's see if that tells us anything.

The LWP's HOWTO tells you how to configure things using the xsetwacom commands (which you would put into wacomcpl's .xinitrc) here:  [http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)  Section 9.0.

---

### Post by tudor117 on 2009-09-11
So, using "xsetwacom set stylus Button2 '#'" still has the same effect; Button2 changes both buttons.
```
$ xinput get-button-map "stylus"
1 2 3 4 5 6 7
$ xinput get-button-map "pad"
1 2 3 4 5 6 
$ xinput get-button-map "cursor"
1 2 3 4 5 6 7 
$ xinput get-button-map "eraser"
1 2 3 4 5 6 7   
```Hope it can be fixed.

---

### Post by Favux on 2009-09-11
Hi tudor117,

OK, that's different from what happens when I do it.  If I use the command with say "stylus" I get the same output as with 'help'.  I assume this means the stylus button is being mapped through linuxwacom.  The ouput you're getting is what you would get with a mouse.  I don't know why it isn't mapping through wacomcpl/xsetwacom for you or how to get it to do that.  I would have thought either .fdi would do that for you.

So to change the mapping I guess you could use, to say make the first button a right click and the second a middle click, the same xinput command you'd use with a mouse:
```
xinput set-button-map "stylus" 1 3 2 4 5 6 7
```

And then plug the line into ~/.xstartup or other init file.  Maybe wacomcpl's .xinitrc?

From:  [https://wiki.ubuntu.com/X/Config/Input#Example:%20Disabling%20middle-mouse%20button%20paste%20on%20a%20scrollwheel%20mouse](https://wiki.ubuntu.com/X/Config/Input#Example:%20Disabling%20middle-mouse%20button%20paste%20on%20a%20scrollwheel%20mouse)  And you'll want to take a look at the rest of the wiki.

I sure would rather do it through wacomcpl.  Any thoughts?

---

### Post by antario91 on 2009-09-12
Hi Again!
I don't know, Favux, but my xinput does not have a get-button-map attribute. (This means, that I did't find it in the help and I get the help message whenever I use get-button-map) :confused:

---

### Post by Favux on 2009-09-12
Hi antario91,

That sounds like what I get.  So is linuxwacom in charge of your button map?  I am confused.  Why would tudor117 be getting a different output?  I know tudor117 used a button map command, but it wasn't installed anywhere to be permanent.  And it's the same tablet.  I am very confused.

---

### Post by Favux on 2009-09-12
Hi antario91 & tudor117,

If wacomcpl won't configure the stylus buttons then maybe we can do it through the 10-wacom.fdi like you used to with xorg.conf.  We could try adding:
```
            <merge key="input.x11_options.Button2" type="string">3</merge>
            <merge key="input.x11_options.Button3" type="string">2</merge>
```
Which makes the first stylus button a right mouse click and the second one a middle mouse click.  Put the lines here:
```
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
            <merge key="input.x11_options.Button2" type="string">3</merge>
            <merge key="input.x11_options.Button3" type="string">2</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
```
Now since .xinitrc (wacomcpl) is executing last it should control.  But if it is not doing anything?  Worth a shot anyway.

---

### Post by tudor117 on 2009-09-12
Hi Favux,

Everything that you listed, had the same result as before
But the last method, with the fdi, doesn't show a different get-input-map from xinput even if it is altered in the fdi (that was supposed to happen right?) whereas the "set-button-map" did change the mapping from xinput.

So here's the thing. When I first got the tablet and plugged it in, it worked out of the box as a cursor/mouse. The only things missing where pressure sensitivity and the buttons. So far I left it like that (i.e. Gimp is set to screen not window), so that may be what's different than antario91. Or if we both have that, that may be the reason why it's acting weird.
Any ideas?

---

### Post by Favux on 2009-09-12
Hi tudor117,

> When I first got the tablet and plugged it in, it worked out of the box as a cursor/mouse. The only things missing where pressure sensitivity and the buttons. So far I left it like that (i.e. Gimp is set to screen not window), so that may be what's different than antario91.
I'm pretty sure I don't understand what you just said, but here goes.

Well sure.  If you didn't install the Waltop version of the 10-wacom.fdi I posted then that's the difference.  Jaunty is configuring your tablet as a mouse in that case.  That is what you're saying, isn't it?

I thought you had installed the waltop wacom.fdi

---

### Post by tudor117 on 2009-09-12
Sorry about that. I was saying that when I first got the tablet it worked as a mouse. I thought it needed a driver and it wouldn't do anything at all without one.

But, I did install the fdi you posted a long time ago. It's been installed ever since.

However, the important part was that none of the commands worked. So is ubuntu seeing both buttons as one?

---

### Post by Favux on 2009-09-12
Hi tudor117,

Thanks, that cleared it up.  We're where I though we were.

So you're saying the button lines for the .fdi didn't change anything for you.  I guess we're stuck unless we come up with a brainstorm.

But you've got pressure in Blender and Gimp and use of "one" stylus button.  So major improvement.

By the way no one has yet said if they are able to configure their pad (the buttons on the tablet) yet.

What is the output of "xsetwacom list" entered in a terminal?

Edit:  And you rebooted after adding the button lines to the .fdi?

---

### Post by tudor117 on 2009-09-12
>  I guess we're stuck unless we come up with a brainstorm. How do we do that? I'm kinda new to brainstorming...

However, we did get major improvements which is great!

> By the way no one has yet said if they are able to configure their pad (the buttons on the tablet) yet. So this is the hardest part to explain. And since a picture is worth a thousand words, I attached one (couldn't find any on net).

In the picture you can see the pen buttons. You can also see a border with funky looking rectangles. Those are supposed to be the "buttons". In windows and mac it's theres a driver which manages them. The only way to press them are with the pen tip. I was supposed to put a paper they gave me underneath which displays what does what. There's a xp version, vista version and mac version. No linux. So, I refused to use it. As well, the "buttons" aren't part of the workspace (in my current configuration). The workspace ends at the border where the buttons start.

I also found a better picture on ebay which I attached too because it won't remain there forever. In that picture you can see one of the windows templates.

And here's the list as requested.
```
$ xsetwacom list
eraser           eraser    
cursor           cursor    
pad              pad       
stylus           stylus   
```

---

### Post by Favux on 2009-09-12
Hi tudor117,

I guess it's the opposite of a brain fart, which is what I'm currently having.

I can't quite see the stylus buttons well enough.  Could be a rocker switch for all I can tell.

The tablet buttons don't look like a Wacom pad.  So I guess not too surprising if they don't work with "pad".  And you have to touch them with the stylus tip, which is not what you do with a Wacom button.  I wonder if the stylus is necessary.  Would any small thing do, or does it have to be the stylus tip?

Well with xsetwacom list we "shouldn't" be seeing duplicates.  I wonder if antario91 sees that too?  You're sure you don't have a custom_wacom.fdi or some other tablet type .fdi installed?

---

### Post by tudor117 on 2009-09-12
Hello,

Well I found the tablet at [http://www.geniusnet.com/](http://www.geniusnet.com/)
If you go to tablets than G-Pen F610 it gives a much better in depth explanation than me. All with better pictures.
My old webcam + skills = bad pictures

> 
 I guess it's the opposite of a brain fart, which is what I'm currently having.Oh! I thought you meant ubuntu brainstorm wise. If it's regular brainstorm I'll let you know if I think of anything.

> I wonder if the stylus is necessary. Would any small thing do, or does it have to be the stylus tip?It needs to be the stylus because it is part of that "magic surface". It is not a physical button.
The program that takes care of button pressed on the other OS's is called Macro Key Manager (about this at their website).

As for other fdi's I haven't added any so only the default one's should be present.

---

### Post by Favux on 2009-09-12
Hi tudor117,

Not Ubuntu Brainstorm.  A regular one.

That's what I thought.  So my guess is those tablet buttons may need a driver specifically for them.

I've seen duplicates in xsetwacom list before.  I'm trying to remember the context.  It may be when we were trying to come up with the .fdi and hadn't cleanly separated things out with:
```
    <match key="input.originating_device" contains="if0">
```
I think maybe we were still pulling in stuff from another section with "if1"?

Ouch.  Maybe we need to look at lshal after all?  I sure don't want to.

---

### Post by tudor117 on 2009-09-12
Hello

Ok for brainstorming, there was this tool that tells you when a button is pressed and what is pressed. I used it a long time ago when I wanted to configure a remote with ubuntu. But in jaunty it works out of the box. Anyways something like that could maybe tell you if there's a difference between button presses?

Those are doubles!?!? I thought it was telling me "eraser" as an eraser and etc
Wow..   So how can we fix it?

---

### Post by Favux on 2009-09-12
Hi tudor117,

If you remember the tool and can make sense of the output.

For the double output you'd have to do the "lshal>lshal.txt thing I talked about earlier.  Compress it and attach it to a post.  Then we'd have to find the sections related to your tablet and see if we could come up with a match line(s) that would give us what we need.  Lot's of work with no guarantee.  Might want it with and without the wacom.fdi too.

---

### Post by tudor117 on 2009-09-12
Hey,

The tool was a standard ubuntu command. I just can't remember...
I'll look for it in the meantime.

So, how can I help?

---

### Post by tudor117 on 2009-09-12
So I found what it was.
It was irw. Which is a lirc tool which will not work.
I also found "xev" but it shows what x is getting and x is getting the  same button press for both buttons.

---

### Post by Favux on 2009-09-12
Hi tudor117,

At first pass there look to be six sections:
```
udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_50d_237_noserial'  (string)
  info.product = 'Slim Tablet'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial'  (string)
  info.vendor = 'WALTOP International Corp.'  (string)
  linux.device_file = '/dev/bus/usb/001/010'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.7'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 4357  (0x1105)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 10  (0xa)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.7'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Slim Tablet'  (string)
  usb_device.product_id = 52  (0x34)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'WALTOP International Corp.'  (string)
  usb_device.vendor_id = 5935  (0x172f)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.7/1-3.7:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 4357  (0x1105)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 10  (0xa)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.7/1-3.7:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 52  (0x34)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'WALTOP International Corp.'  (string)
  usb.vendor_id = 5935  (0x172f)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'
  access_control.file = '/dev/input/event3'  (string)
  access_control.type = 'mouse'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard', 'hal-acl-tool --add-device', 'hal-setup-wacom'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.mouse', 'input.tablet', 'button', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  input.product = 'WALTOP International Corp. Slim Tablet'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Button2 = '3'  (string)
  input.x11_options.Button3 = '2'  (string)
  input.x11_options.Type = 'stylus'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.7/1-3.7:1.0/input/input13/event3'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'  (string)
  info.product = 'pad'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input_subdev_1'  (string)
  input.device = '/dev/input/event3'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'pad'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'  (string)
  info.product = 'cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input_subdev_0'  (string)
  input.device = '/dev/input/event3'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input_subdev'  (string)
  input.device = '/dev/input/event3'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'eraser'  (string)
```
The last three from the .fdi obviously.  So let me ask this:  You have a stylus with two buttons correct?  Does it have an eraser?  Do you have a Waltop mouse (like a Wacom mouse) for the tablet?  And we have to wonder what the point of "pad" is.

You could look through lshal (using find or by eye) given the sections we've found and make sure I'm not missing any others.

---

### Post by tudor117 on 2009-09-12
Hiya!

So I have a:
-stylus with two buttons
-NO eraser
-NO mouse
-NO physical buttons on pad

So all it is is a simple tablet and pen with two puttons.
I will look through lshal now.

EDIT: I don't think anything was missed.

---

### Post by Favux on 2009-09-12
Well maybe we should just simplify the .fdi as a first step and see if removing the info.callouts.add".  Maybe hal-setup-wacom with the linuxwacom pad is interfering with setting up your stylus buttons?

---

### Post by tudor117 on 2009-09-13
You could say it's better than before. I only removed "info.callouts.add", nothing else and no there are only two styluses.
```
$ xsetwacom list
stylus           stylus 
```But still the buttons refuse to work properly. Using wacomcpl changing button2 changes everything.

---

### Post by Favux on 2009-09-13
OK, test this out in Blender and Gimp etc.  See if wacomcpl still works and now lets you set the stylus buttons.

You can try xsetwacom list and xinput --list too.  Maybe also add the button lines back in if wacomcpl doesn't work.

---

### Post by tudor117 on 2009-09-13
It works exactly as before. Pressure and everything but both buttons change.
```
$ xsetwacom list
stylus           stylus 

$ xinput --list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"stylus"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 20000
        Resolution is 1016
    Axis 1 :
        Min_value is 0
        Max_value is 12500
        Resolution is 1016
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1

```Oh and I thought maybe button1 is on of my buttons (oddly mapped or something) and I found out it wasn't. It was the tip of the pen just as you told me!

---

### Post by Favux on 2009-09-13
Hi tudor117,

I noticed something looking at the lshal.  By any chance do you have the tablet plugged into a usb hub?  If so don't, plug it directly into a usb port on your computer and reboot and check things out.

---

### Post by tudor117 on 2009-09-13
Yea it is now.
But previously, ie when the problem started, it was directly in computer. The reason was that I ran out of usb ports.
Anyways I'll try it again in my computer.

EDIT: No difference.

---

### Post by Favux on 2009-09-13
Hi tudor117,

OK, but with a tablet not a good idea to use a hub.  It can mess things up.

Looks like the original .fdi was as good as we can do.  It's better because it is a more general Waltop .fdi.

Nothing is jumping out at me.  The match lines look good.  I'll look some more but it may be as good as it gets.

So bottom line functioning stylus and one button.  I don't know why we can't get the other one working.

---

### Post by tudor117 on 2009-09-13
Hyers!

So far I haven't found any problems with the hub and all. But I moved it anyways.
Even if this is as good as it gets, it's still a drastic improvement compared to where I started. So, I must say THANK YOU FAVUX :)

---

### Post by Favux on 2009-09-13
Hi tudor117,

Your welcome.

Nothing else is coming to mind.

Especially when experimenting with it a hub is probably not a good idea.  But once you stop fiddling with it and if you need the ports and the hub isn't causing a problem, why not?  And if it starts behaving weird you'll know why.

---

### Post by Jarretinha on 2009-10-22
Hi everyone,

I've acquired a C3 Tech tablet which is effectively a Waltop Slim Tablet and stumbled upon this thread. I've tried every single tip around and was unable to get my device on xinput. 

Someone already tried the linux driver at Waltop site? I was unable to make it work on Karmic.

By the way, it seems that my tablet is being treated as a mouse only. Where did I miss the point?

---

### Post by tudor117 on 2009-10-22
Hi Jarretinha,
I used the drivers in the repos. I haven't tried it on Karmic yet, but I'm eager to when the final release comes out.
So when you say you tried everything what exactly did you do?
And which programs are you trying to use it with?

---

### Post by Favux on 2009-10-22
Hi Jarretinha,

Welcome to the Ubuntu Forums!

We could take a look at the default 10-linuxwacom.fdi that comes with Karmic.  The Jaunty one, 10-wacom.fdi, has entries for Waltop and N-trig.  Oh, and did you catch the name change for the .fdi?

I assume this means the Ubuntu dev.s in Jaunty patched the wcmUSB.c to see those two Vendor ID's.  Or something similar.  There's a table of Vendor and Product ID's in wcmUSB.c.  If the Waltop isn't in there you're probably locked out of the linuxwacom drivers.

---

### Post by Jarretinha on 2009-10-26
I've tried to compile the driver from linuxwacom, to rebuild from source the packages wacom-tools and xserver-xorg-input-wacom, the aiptek variant and the fdi method. After building the linuxwacom and cp the driver to the right place, just pluging my tablet breaks Xorg and issues an error (smth like 172f vendor not supported). 

My idea is to use gimp/inkscape/blender and to use the tablet as a mouse substitute to reduce the strain in my wrists.

Any ideas?

---

### Post by Favux on 2009-10-26
Hi Jarretinha,

I think you might almost have it working.  Does this look familiar?:
> If after compiling and installing your new hid-ntrig.ko the n-trig digitizer is still not working correctly you may need to compile and install linuxwacom. It probably means the Ubuntu dev.s haven't applied the n-trig.patch (attached below) to wcmUSB.c (in the linuxwacom source code). The wcmUSB.c has a "table" of Vendor and Product ID's for Wacom USB devices and if unpatched will return "wacom driver does not support 1b96" on encountering the n-trig digitizer (trying to use the linuxwacom drivers). So the patch needs to be applied to the current 0.8.4-3 linuxwacom from the LWP.
From this HOW TO:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)

If you use 'lsusb' and/or 'lshal' you should be able to find your Vendor and Product ID's and add them to the table.  The n-trig.patch attached at the bottom of the HOW TO should show you how.  You don't need to change that many lines.  Or you could substitute your information into the n-trig.patch, rename it waltop.patch and apply it according to the instructions in the HOW TO.

With any luck it should work.

---

### Post by Jarretinha on 2009-10-26
Hi Favux,

Well, I've added the waltop slim tablet to the list in wcmUSB.c and compiled it. The Xorg stopped crashing (I'm not sure why, I didn't add the vendor_id). The buttons don't work properly. GIMP says that it do not has permssion to open the device. The cursor is OK. What am I missing?

A piece of my lshal . . .

---

### Post by Favux on 2009-10-26
Hi Jarretinha,

By cursor do you mean the tablet stylus?  In linuxwacom the cursor refers to the Wacom tablet mouse not the stylus.  So the stylus is working, just not in Gimp.  Have you tried it in Xournal or Inkscape?

Lets look at:
```
xinput --list
```
and see what your Xorg.0.log.

We're looking to see if the linuxwacom driver is attaching to your tablet.

Edit:  Oh, and the changes you made to wcmUSB.c and your 'lsusb' referring to your C3 Tech/Waltop Slim tablet.

---

### Post by Jarretinha on 2009-10-26
Hi again,

Files attached.

In wcmUSB.c I've just added a single line:

{ 0x32, 2540, 2540, &usbTabletPC   }  /* TabletPC 0x32 */

By cursor I mean the mouse like behaviour of the stylus. I can control the pointer, but no buttons. It's not working anywhere. GIMP is the only one that acuses some problem (and eventually crashes).

---

### Post by Favux on 2009-10-26
Files didn't attach.  You mean the stylus buttons right?  Are there two of them?  It will be a while before I can get to this.

Please add the part of lusb for the tablet, I want to see how's it's identifying the tablet.

Edit:  The changes you made were not enough it looks like.  Both xinput and Xorg.0.log are showing that a touchpad .fdi is configuring your tablet and linuxwacom drivers aren't attaching.

---

### Post by Jarretinha on 2009-10-26
I don't get it. It do recognize the piece and the vendor. The stylus do work and the buttons send some signal but they do not seem to be interpreted correctly. I've filed the problem initially as a bug (cf. [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/458609]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/458609"). Could gsynaptics interfering with the configuration?

---

### Post by Favux on 2009-10-26
Hi Jarretinha,

Good point.  Actually it could.  See the advice Ayuthia gives markkupaakkonen in post #205 here:  [http://ubuntuforums.org/showthread.php?t=1252492&page=21](http://ubuntuforums.org/showthread.php?t=1252492&page=21)

It would be sweet if that's it.  I guess we would have to look at lshal to see if the Synaptics .fdi is grabbing your tablet too.  Although the change he suggests to the .fdi probably won't hurt anything.

---

### Post by Jarretinha on 2009-10-26
Tried the suggestion. Still same behaviour. Is there any reason to Xorg finding 9 buttons?

(II) WALTOP International Corp. Slim Tablet: Found 9 mouse buttons

And why is it configured as a touchpad?

The stylus has only two buttons and the pad has 10 pseudo-buttons. 

Any idea about the meaning of this error?

(WW) WALTOP International Corp. Slim Tablet: unable to handle keycode 331

---

### Post by Favux on 2009-10-26
Hi Jarretinha,

Well like I said, maybe not enough changes.  The patch changes/adds 4 lines (+) two of which you need to edit.  Either directly or through a patch.  And removes 3 lines (-).  So let's call this waltop.patch:
```
--- linuxwacom-dev/src/xdrv/wcmUSB.c	2009-05-08 04:38:23.974349447 -0400
+++ linuxwacom-dev.patched/src/xdrv/wcmUSB.c	2009-05-08 04:38:17.712127356 -0400
@@ -507,7 +507,8 @@
 
 	{ 0x90, 2540, 2540, &usbTabletPC   }, /* TabletPC 0x90 */ 
 	{ 0x93, 2540, 2540, &usbTabletPC   }, /* TabletPC 0x93 */
-	{ 0x9A, 2540, 2540, &usbTabletPC   }  /* TabletPC 0x9A */
+	{ 0x9A, 2540, 2540, &usbTabletPC   },  /* TabletPC 0x9A */
+	{ 0x1, 935, 1122, &usbTabletPC   }  /* TabletPC 0x9A */
## 	{ 0x32, 2032, 2032, &usbGraphire4  } /* Waltop Slim */
###	{ 0x16, 2032, 2032, &usbGraphire4  }, /* Graphire4 6x8 */ 
 };
 
 Bool usbWcmInit(LocalDevicePtr local, char* id, float *version)
@@ -526,7 +527,7 @@
 	ioctl(local->fd, EVIOCGNAME(sizeof(id)), id);
 
 	/* vendor is wacom */
-	if (sID[1] == 0x056A)
+	if (sID[1] == 0x056A || sID[1] == 0x1b96)
##	if (sID[1] == 0x056A || sID[1] == 0x172f)
 	{
 		common->tablet_id = sID[2];
 
@@ -549,7 +550,7 @@
 			common->wcmCapacityDefault = -1; 
 		}
 
-		if (common->tablet_id == 0x9A || common->tablet_id == 0x93 || common->tablet_id == 0x90)
+		if (common->tablet_id == 0x9A || common->tablet_id == 0x93 || common->tablet_id == 0x90 || common->tablet_id==1)
 		{
 			if (common->tablet_id != 0x90)
 			{
```
Notice if you edit directly it tells you the line numbers.  Anyway the lines marked with '##' are right below the n-trig lines you need to substitute for (which are being added by the patch).  Then rather than a tablet pc I picked at semi-random a graphire tablet since I have no idea about the size or spec.s of your Waltop.  Hope I get lucky.  The line I stole it from is marked with '###'.  If you want to use the 'patch' you need to remove the lines commented (#) after making the changes.

The other thing to worry about is "2540, 2540," or what I changed to " 2032, 2032,".  That's suppose to be your tablet's resolution.  So you need to change that to reflect what the Slimline's actual resolution is.

Then you could go on to, based on your tablet spec.s as Alexia at linuxwacom said:
> Your box should have the DPI of your tablet and your tablets active area is 5.8 x 3.6 in in size. Wacom says its resolution is 2540dpi so X/Y are calcualtable, X is 5.8*2540=14732 and Y is 3.6*2540=9144. It has. has 512 steps of pressure, so 511 is correct in the conf. 
calculate the coordinates.

I hope you understand what I'm trying to say here.

---

### Post by tudor117 on 2009-10-31
Hi Favux,
After upgrading to Karmic (clean install), my tablet no longer works. I realized I had to change the fdi to what I used to have and once I did, as soon as I plug my tablet in X crashes and continues to crash until the tablet is unplugged. 
Does that mean I need to compile the driver or is there an easier way?

**

---

### Post by Favux on 2009-11-01
Hi tudor117,

Did you catch that the .fdi name changed from 10-wacom.fdi to 10-linuxwacom.fdi?  So make sure the .fdi we came up with is labeled 10-linuxwacom.fdi.  Don't want both.

Looking at my Karmic install the default 10-linuxwacom.fdi doesn't have Waltop in it like the Jaunty .fdi did.  Searching Synaptic Package Manager doesn't show a Waltop driver.

So it looks like the crash is because of the wacom driver not recognizing waltop.  In other words X blows up when the .fdi tries to load the wacom driver.  Unless you had the two wacom.fdi's.

So it looks like the only way to get it to work would be to try and patch and compile linuxwacom  like Jarretinha was trying.  You could also post a bug report and see if the Ubuntu dev.s can bail you out.  After all they had Waltop working in Jaunty.

---

### Post by tudor117 on 2009-11-01
Hi Favux,
I noticed the name change as I was looking through posts. But it still doesn't work.

However, I reinstalled the wizardpen driver as i noticed Jarretinha had alot of problems compiling. The wizardpen driver isn't too bad but I can't use my mouse in gimp as a drawing tool when the tablet is used and it doesn't work in Blender.
Nor do my buttons do anything.

I suppose I'll give it a try compiling it.

---

### Post by tudor117 on 2009-11-01
Just a quick question. Do I compile the source from the repos or the ones from linuxwacom website?
And, should I compile or would a simple install of the driver work?

---

### Post by Favux on 2009-11-01
Hi tudor117,

You could do either I suppose.  I usually compile (0.8.4-3) from the LWP site.

But first you probably have to patch the wcmUSB.c.  It would be nice to know what they did for sure in 0.8.2-2 to support Waltop.  Maybe look at the Jaunty wcmUSB.c source so you could just imitate the changes they made to support Waltop for your patch.

---

### Post by tudor117 on 2009-11-01
Hi Favux,

I compiled the newer drivers with out any changes and it obviously didn't work. 
The older drivers wouldn't compile. So I tried the new drivers with the old wcmUSB.c but it still crashed.
The two files themselves aren't that very different. There are minor changes along with some new definitions and renaming some tablets (i.e. "USB Intuos" -> "USB Intuos1")

Actually they added an exit if vendor isn't wacom. I'll try to remove that and recompile.

EDIT: So I took commented out the return but now it just doesnt work. At least it doesn't crash X though. An other question is, should I be compiling with kernel module?

---

### Post by Favux on 2009-11-01
Hi tudor117,

> Actually they added an exit if vendor isn't wacom. I'll try to remove that and recompile.
So I took commented out the return but now it just doesnt work. At least it doesn't crash X though.
Good.  Actually everyone should see that.  Can you post it?

> should I be compiling with kernel module? 
Not sure what you're asking.  You want to compile a wacom.ko and install it in place since your tablet is usb.

---

### Post by tudor117 on 2009-11-01
Hi

```

if (common->tablet_id == 0x9A || common->tablet_id == 0x93 || common->tablet_id == 0x90)
        {
        //bunch of code here
}
else
    {
        ErrorF("%x is not supported by linuxwacom.\n", sID[1]);
        return FALSE;
    }

```I commented the "return FALSE;" though i doubt it does much.
I uploaded the changed file.

As for the kernel module:
> 
**Note2**: if you also want to install the wacom kernel module, you need to add --enable-wacom to the ./configure line. This usually isn't necessary unless you are using an older kernel which does not support your tablet. In this case the line would be: 

```
./configure --enable-wacom --prefix=/usr
```That was taken from [https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver)

Looking through again, the newer file also changes the ways events are handled a tiny bit.

---

### Post by Favux on 2009-11-01
Hi tudor117,

Right and you want to:
```
sudo cp ./src/2.6.31/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
From this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  You might want to skim through it.

---

### Post by tudor117 on 2009-11-01
Hi Favux,

It seems like there's quite a lot to do. I'll try it soon. Would I need to recompile it every time the kernel updates?

And another thing I noticed was that running wacomcpl tells me that I have a stylus and I can configure it. However, in the screen mapping, the Display mapping option is grayed out. I cannot move my stylus at all.
I'm hoping it's fixable without compiling every time I update. Nevertheless I'll give it a try.

---

### Post by Favux on 2009-11-01
Hi tudor117,

Well once things settle down new kernels only come through every few weeks or so.  That's the beauty of a HOW TO.  I can run through it in about 5 minutes so no big deal.

Besides you won't want to "make install".  At most you'll only need to compile a new wacom.ko.  But you may be able to get away with copying the wacom.ko you compile from the source code into the new kernel location without recompiling it.  If you have to recompile you'd skip at least:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom

sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
Because you don't need a new version of linuxwacom.  The patched 0.8.4-3 will be just fine.

---

### Post by tudor117 on 2009-11-01
Hi Favux,

I tried with the new compiled driver but nothing happens. It doesn't crash but it still doesn't work. wacomcpl sees "stylus" but configuring it does nothing. Once I unplug the tablet the "stylus" disappears but nothing else changes. It just doesn't work.
I'll try to look more in the two different files.

Is wcmUSB.c the only file that should be changed?

---

### Post by Favux on 2009-11-01
Hi tudor117,

No there could be other files that need changing.  We're trying to add the new Wacom Bamboo Pen & Touches on this [thread]("http://ubuntuforums.org/showthread.php?t=1290251").  The second post has a link to the patches Ayuthia has come up with.

But I can't believe the Ubuntu dev.s did all that for Jaunty.  I'd think it was a simple change.  So:
-post the changes you made to wcmUSB.c like I did in post #55
-maybe I guessed the wrong Wacom tablet and the Waltop emulates a Graphire3 or 2 or something and not a Graphire4.
-maybe you don't have the correct resolution for your tablet.  How did you come up with it?
-just the fact that wacomcpl sees it would seem to indicate you are close.

If "xinput --list" calls the stylus an ExtensionKeyboard rather than an ExtensionPointer then the linuxwacom drivers are picking your tablet up.  You can confirm that in Xorg.0.log.

---

### Post by tudor117 on 2009-11-02
Hi Favux,

Here is my attempt to the changes:
```
 @@ -580,7 +580,6 @@
     else
     {
         ErrorF("%x is not supported by linuxwacom.\n", sID[1]);
-        //return FALSE;
     }
 
     if (!common->wcmModel)

```The point is that there is "//" in front of return FALSE. Not sure if this is removing or adding the //.

I used the fdi file from post #36, the one you attached.

You're right, xinput calls the stylus ExtensionKeyboard. Here is the Xorg.0.log:
```

(II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-3 $
(**) stylus: always reports core events
(**) stylus device is /dev/input/event5
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/event5"
stylus Wacom X driver grabbed event device
172f is not supported by linuxwacom.
(==) Wacom using pressure threshold of 61 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=20000 maxY=12500 maxZ=1023 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=20000 bottom Y=12500 resol X=1016 resol Y=1016

```

---

### Post by Favux on 2009-11-02
Hi tudor117,

Ok, that means the linuxwacom driver isn't attaching.  The next few lines below what you posted probably show that.  It says:
```
(**) Option "Device" "/dev/input/event5"
stylus Wacom X driver grabbed event device
172f is not supported by linuxwacom.
```
To be sure we are on the same page if you look at what I posted in [post #55]("http://ubuntuforums.org/showpost.php?p=8171601&postcount=55").
You change line:
```
-	{ 0x9A, 2540, 2540, &usbTabletPC   }  /* TabletPC 0x9A */

```
to
```
+	{ 0x9A, 2540, 2540, &usbTabletPC   },  /* TabletPC 0x9A */
```
Notice the comma.
Then you add right below it:
```
 	{ 0x32, 2032, 2032, &usbGraphire4  } /* Waltop Slim */

```
assuming your tablet resolution is 2032, 2032.

Next you change:
```
-	if (sID[1] == 0x056A)
```
to
```
	if (sID[1] == 0x056A || sID[1] == 0x172f)
```
Then finally:
```
-		if (common->tablet_id == 0x9A || common->tablet_id == 0x93 || common->tablet_id == 0x90)
```
to
```
+		if (common->tablet_id == 0x9A || common->tablet_id == 0x93 || common->tablet_id == 0x90 || common->tablet_id==1)

```
You don't actually enter the - or + at the beginning of the lines, that's just the diff telling you which lines are removed/changed and which are added.  And I don't think you want/need the change you made.

Oops!  I just realized there's a problem with that last line.  The first line would have to begin with "{ 0x9A,".  The n-trig was imitating a tablet pc not a graphics tablet.  Darn.  We'll have to look at wcmUSB.c to figure that out.

---

### Post by tudor117 on 2009-11-02
Hi Favux,

I undid my change and redid your changes. As you suspected, it didn't work. However it also didn't crash.
Is there any log that gets updated as soon as I replug my tablet? It would be very helpful.

---

### Post by Favux on 2009-11-02
Hi tudor117,

Sure with Xorg.0.log.  We were just use ExtensionKeyboard in xinput as a proxy.  And also /var/log/messages esp. if we add:
```
	<merge key="input.x11_options.DebugLevel" type="string">12</merge>
```
and/or
```
	<merge key="input.x11_options.CommonDBG" type="string">12</merge>
```
to the .fdi.  Should spit out a lot of stuff if linuxwacom attaches.

---

### Post by tudor117 on 2009-11-02
Hi Favux,

Okay, that's good, now I have alot of messages from linuxwacom. However, xinput still sees ExtensionKeyboard.
```
"stylus"    id=4    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 7
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 20000
        Resolution is 1016
    Axis 1 :
        Min_value is 0
        Max_value is 12500
        Resolution is 1016
    Axis 2 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1

```EDIT: Thought this might be important (from xorg.0.log)
```

xf86WcmUninit
(II) UnloadModule: "wacom"
(II) config/hal: Adding input device stylus
(**) stylus: always reports core events
(**) stylus device is /dev/input/event5
(**) Option "DebugLevel" "12"
(**) WACOM: stylus debug level set to 12
(**) Option "CommonDBG" "12"
(**) WACOM: stylus tablet common debug level set to 12
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
BEGIN xf86WcmProc dev=0x1be8ee0 priv=0x1559920 type=stylus(stylus) flags=16641 fd=-1 what=INIT
xf86WcmDevOpen
opening /dev/input/event5
(**) Option "Device" "/dev/input/event5"
usbDetect
stylus Wacom X driver grabbed event device
initializing USB tablet
172f is not supported by linuxwacom.
(==) Wacom using pressure threshold of 61 for button 1
Tablet does not support setting link speed, or not yet implemented
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=20000 maxY=12500 maxZ=1023 resX=1016 resY=1016  tilt=enabled
usbDetectConfig 
xf86WcmRegisterX11Devices (stylus) 7 buttons, 7 keys, 6 axes
xf86WcmInitArea
xf86WcmInitialScreens for "stylus" number of screen=1 
xf86WcmInitialScreens for "stylus" topX[0]=0 topY[0]=0 bottomX[0]=1680 bottomY[0]=1050 
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=20000 bottom Y=12500 resol X=1016 resol Y=1016
xf86WcmRotateTablet for "stylus" 
rotateOneTool for "stylus" 
xf86WcmMappingFactor 
xf86WcmVirtaulTabletSize for "stylus" x=20000 y=12500 
xf86WcmMappingFactor Active tablet area x=20000 y=12500 (virtual tablet area x=20000 y=12500) map to maxWidth =1680 maxHeight =1050
X factor = 0.084, Y factor = 0.084
xf86WcmMappingFactor 
xf86WcmVirtaulTabletSize for "stylus" x=20000 y=12500 
xf86WcmMappingFactor Active tablet area x=20000 y=12500 (virtual tablet area x=20000 y=12500) map to maxWidth =1680 maxHeight =1050
X factor = 0.084, Y factor = 0.084
END xf86WcmProc Success 
BEGIN xf86WcmProc dev=0x1be8ee0 priv=0x1559920 type=stylus(stylus) flags=16641 fd=23 what=ON
xf86WcmDevOpen
```

---

### Post by Favux on 2009-11-02
Perfect, that's what we want.  ExtensionPointer would mean a mouse .fdi has it.  Let me look.

We're still getting "172f is not supported by linuxwacom".  Does the stylus do anything now?

---

### Post by tudor117 on 2009-11-02
The stylus still doesn't do anything. No moving the cursor, no clicking, nothing.

Not sure if this means anything, but it says Mouse. From (messages)
```

Nov  2 22:06:33 tudor-desktop kernel: [ 8314.021353] generic-usb 0003:172F:0034.000A: input,hidraw2: USB HID v1.10 Mouse [WALTOP International Corp. Slim Tablet] on usb-0000:00:02.0-9/input0

```I attached my fdi in case you wanted to look.

---

### Post by Favux on 2009-11-02
Hi tudor117,

OK, I'm going to have to sit down and look through all of this and see if I can figure out where we're going wrong.

What would be very helpful is if you knew the resolution of your tablet.  Also the pressure levels, like 512 or 1024 or whatever.  Also the active area (size) in inches.

In the meantime I found the Waltop site with a linux driver.  Maybe you could try it and/or we can look at it.  It's located [here]("http://www.waltop.com/download.asp?lv=0&id=2").  I haven't look to see if there's a faq for linux.  Maybe a readme.txt in the download?

---

### Post by tudor117 on 2009-11-03
Hi Favux,

I haven't thought of looking for a waltop driver yet :P Good idea.
However, it's fairly complicated and it uses xorg configuration.
I posted the readme that's ubuntu related.
The tablet has 1024 pressure levels, a 6" x 10" working area, a resolution of 2000 LPI, and a max report rate of 125 points/sec.

README for waltop driver:
```

0  USB HID  
------------
Ubuntu 
 
0.2.1  Copy hid-xxx.c to kernel source code directory 
Consult 0.1.1 
 
 
0.2.2  Rebuild (usb)hid.ko 
#make 
 
 
0.2.3  Install (usb)hid.ko 
#make install 
#make modules_install 
 
Or Copy (usb)hid.ko to kernel module directory 
 
 
0.2.4  Reboot Linux 
 
 
 
1  Compile 
------------ 
 
#make 
 
 
 
2  Install Waltop Linux Driver (waltoptablet.ko) 
------------ 
 
Linux Kernel version 2.6.21: 
#cp .\waltoptablet.ko /lib/modules/$(shell uname -r)/kernel/drivers/input 
 
Linux Kernel version 2.6.23 and above: 
#cp .\waltoptablet.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/tablet 
 
 
 
3  Register Linux kernel driver 
------------ 
 
#cd /lib/modules/'uname -r'/drivers/input 
#/sbin/insmod ./waltoptablet.ko 
#/sbin/depmod -e 
 
 
 
4  List the registered module 
------------ 
 
#/sbin/lsmod | grep waltop 
 
 
 
5  Plug-in the tablet device  
------------ 
 
 
 
6  Test tablet controller detection (waltoptablet.ko) 
------------ 
 
#more /proc/bus/usb/devices 
 
... 
... Driver=waltoptablet.ko 
... 
 
6.1  If Driver=usbhid, add the waltop vendor id to the linux kernel 
6.2  If Driver=(none), install the waltop driver 
 
 
 
Or 
 
 
#more /proc/bus/input/devices 
 
I: Bus=xxxx Vendor=172f Product=0034 Version=1105 
N: Name="Slim Tablet" 
P: 
S: Sysfs=/class/input/input6 
H: Handlers=mouse2 event5 
B: 
B: 
 
 
 
 
/***************************************************************************** 
** The Tablet of X11 Driver 
****************************************************************************/ 
 
 
1  Compile 
------------ 
 
#./configure 
#make 
 
 
 
2  Install Waltop X11 driver (waltoptablet_drv.so) 
------------ 
 
#cp .libs/waltoptablet_drv.so /usr/lib/xorg/modules/input 
 
 
 
3  Edit the Configuration file (xorg.conf) 
------------ 
 
3.0  Check Tablet device  event number 
 
The event number will be used  to xorg.conf  "Device" option 
 
#more /proc/bus/input/devices 
 
I: Bus=xxxx Vendor=172f Product=0034 Version=1105 
N: Name="Slim Tablet" 
P: 
S: Sysfs=/class/input/input6 
H: Handlers=mouse2 event5 
B: 
B: 
 
 
3.1 Edit the  xorg.conf 
 
 
3.1.0 Edit the xorg.conf 
 
#vi /etc/X11/xorg.conf 
 
 
3.1.1 Add InputDevice section 
 
Section "InputDevice" 
    Identifier     "WaltopStylus" 
    Driver         "waltoptablet" 
    Option         "Device"    "/dev/input/eventX" 
    Option        "Type"        "stylus" 
    Option        "Mode"        "absolute" 
    Option        "USB"        "on" 
    Option        "KeepShape"     "off" 
    Option        "Pressure"    "Soft" 
    Option        "debuglevel"    "0"     
EndSection 
 
 
/* 
**Attention: 
** 1  Option "Device" "/dev/input/eventX" 
**      X is the event number, consult 3.0 
** 
** 2  Option "Pressure" "string" 
**     string value  { "Soft" | "Hard" | "Linear" } . 
** 
** 3  Option "debuglevel" "number" 
**    number "0 -12",  0 is Off. 
** 
*/ 
 
 
3.1.2 Edit ServerLayout 
 
Add below to ServerLayout: 
 
InputDevice    "WaltopStylus"    "SendCoreEvents" 
 
 
Example: 
 
Section "ServerLayout" 
    Identifier     "single head configuration" 
    Screen      0  "Screen0" 0 0 
    InputDevice    "Keyboard0" "CoreKeyboard" 
    ... 
    InputDevice    "WaltopStylus"    "SendCoreEvents" 
EndSection 
 
 
 
4  Restart X Window 
------------

```

---

### Post by Favux on 2009-11-03
Hi tudor117,

Good, I'll look at that too.  I just googled "waltop linux driver" and it popped up as the first entry.  We should be able to use the xorg.conf or turn it into a .fdi if needed.

Sorry I'm so slow but I'm doing a bunch of chores that look like they'll keep me occupied for another day or so.  I'm trying to squeeze this in.

---

### Post by tudor117 on 2009-11-03
Hi Favux,

I'll try to compile it.

But, finish your chores first and then we'll fix it. Your not the only one who has things to finish ;)

---

### Post by oberonking on 2009-11-03
Mm..... hi Favux
Well, i'm going crazy with my tablet Waltop on karmic, the same issues as tudor.

It's nice to see that exists a waltop driver for linux.... but in the .zip file it's the module for kernel 2.6.27 and in karmic we have 2.6.31, so, it's ok if I use that? 

Subscribed......

---

### Post by Favux on 2009-11-04
Hi oberonking,

If it compiles I suppose it'll be ok.  But 2.6.27 is Intrepid.  2.6.28 was Jaunty.  And the Xorg has been changing.  So it doesn't sound too good.

---

### Post by oberonking on 2009-11-04
> **Favux said:**
> Hi oberonking,

If it compiles I suppose it'll be ok.  But 2.6.27 is Intrepid.  2.6.28 was Jaunty.  And the Xorg has been changing.  So it doesn't sound too good.

this's what I mean.... now, why waltop there isn't suport any more in wacom driver? like in Argentina says "Cosa de mandiga" (devil does)

---

### Post by oberonking on 2009-11-04
Right now i'm using the wizarpen driver.... I have the buttons issue (all work as LMB) but work...
wacom kill my X server.

---

### Post by tudor117 on 2009-11-04
Hi,

The wizardpen driver was ok but it had many problems when I used it. Some of which wouldnt let me use Gimp with the mouse and it wouldn't work in Blender. 
The waltop driver is fairly hard to compile and I really like the wacom tools offered. I'll try to take a look at the wacom source... though I'm not to good of a programmer.
> wacom kill my X server.oberonking, look at the modifications that were made to the source. It's around post _[63]("http://ubuntuforums.org/showpost.php?p=8215662&postcount=63")._

---

### Post by oberonking on 2009-11-04
> **tudor117 said:**
> oberonking, look at the modifications that were made to the source. It's around post _[63]("http://ubuntuforums.org/showpost.php?p=8215662&postcount=63")._

I try it and post the results..... Thanks

---

### Post by tudor117 on 2009-11-04
Hi guys,

OKAY!!! I fixed it. What happened was that we didn't delete the old definition of ```
{ 0x32, 2032, 2032, &usbGraphire4  } /* Waltop Slim */
``` which was higher up in the code: ```
{ 0x32,  508,  508, &usbCintiq     }, /* PL600 */
```I will try to make a diff.... Anyways, if we remove the second line, (and recompile/install) it works to the extent that it was working in Jaunty... which is great but both buttons are the same. YAY!!

Here is my try at it. I used the program EasyDiff but I edited the file so it looks more like what Favux said. Hope it's not too bad. The '+' is what should be added.
```
--- linuxwacom-0.8.4-3/src/xdrv/wcmUSB.c.bak
+++ linuxwacom-0.8.4-3/src/xdrv/wcmUSB.c
@@ -460,7 +460,6 @@
 
     { 0x30,  508,  508, &usbCintiq     }, /* PL400 */
     { 0x31,  508,  508, &usbCintiq     }, /* PL500 */
-    { 0x32,  508,  508, &usbCintiq     }, /* PL600 */
+    //{ 0x32,  508,  508, &usbCintiq     }, /* PL600 */
     { 0x33,  508,  508, &usbCintiq     }, /* PL600SX */
     { 0x34,  508,  508, &usbCintiq     }, /* PL550 */
     { 0x35,  508,  508, &usbCintiq     }, /* PL800 */
@@ -508,8 +507,6 @@
 
     { 0x90, 2540, 2540, &usbTabletPC   }, /* TabletPC 0x90 */ 
     { 0x93, 2540, 2540, &usbTabletPC   }, /* TabletPC 0x93 */
-    { 0x9A, 2540, 2540, &usbTabletPC   }  /* TabletPC 0x9A */
+    { 0x9A, 2540, 2540, &usbTabletPC   },  /* TabletPC 0x9A */
+    { 0x32, 2032, 2032, &usbGraphire4  } /* Waltop Slim */
 };
 
 Bool usbWcmInit(LocalDevicePtr local, char* id, float *version)
@@ -528,7 +525,6 @@
     ioctl(local->fd, EVIOCGNAME(sizeof(id)), id);
 
     /* vendor is wacom */
-    if (sID[1] == 0x056A)
+    if (sID[1] == 0x056A || sID[1] == 0x172f)
     {
         common->tablet_id = sID[2];
 
@@ -551,7 +547,6 @@
             common->wcmCapacityDefault = -1; 
         }

-        if (common->tablet_id == 0x9A || common->tablet_id == 0x93 || common->tablet_id == 0x90) 
+        if (common->tablet_id == 0x9A || common->tablet_id == 0x93 || common->tablet_id == 0x90 || common->tablet_id==1)
         {
             if (common->tablet_id != 0x90)
             {
```

---

### Post by Favux on 2009-11-04
Hi tudor117,

Wow!  You're a genius!

I've been wandering around in the Jaunty Packages source code trying to find a patch called waltop.patch.  Hoping for something simple and obvious.  I was looking at the diff for linuxwacom, which is huge.  There were a couple lines that might be relevant, but not enough context for me to tell.

Please post the patch!

---

### Post by tudor117 on 2009-11-04
Hi Favux,
I posted it in the edit.
Not sure if it's right.
Can you help with that?

---

### Post by Favux on 2009-11-04
Hi tudor117,

Looks like I goofed and chose a Cintiq.  I meant to chose a tablet (like the Graphire4) with buttons on the tablet (pad) to see if that got your pad working.

The diff./changes look good to me.  The way to test it would be to have linuxwacom and the patch on your Desktop and do:
```
patch linuxwacom-0.8.4-3/src/xdrv/wcmUSB.c < waltop.patch
```
Then check the wcmUSB.c to see if the patch applied cleanly.  Be sure to back up the original wcmUSB.c to have it handy.

---

### Post by tudor117 on 2009-11-04
Hi Favux,
Hmmm the patch doesn't work.
I'll try to make one that does work.
It just fails. My other tries just deleted the lines altogether. I'll try again and update this post.

Hmm... I just figured that it works if I make it a diff. But not as a patch.
The diff is:```

--- wcmUSB.c    2009-11-04 16:58:51.312198765 -0500
+++ wcmUSB.c.bak    2009-10-07 09:57:31.000000000 -0400
@@ -460,7 +460,7 @@
 
     { 0x30,  508,  508, &usbCintiq     }, /* PL400 */
     { 0x31,  508,  508, &usbCintiq     }, /* PL500 */
-    //{ 0x32,  508,  508, &usbCintiq     }, /* PL600 */
+    { 0x32,  508,  508, &usbCintiq     }, /* PL600 */
     { 0x33,  508,  508, &usbCintiq     }, /* PL600SX */
     { 0x34,  508,  508, &usbCintiq     }, /* PL550 */
     { 0x35,  508,  508, &usbCintiq     }, /* PL800 */
@@ -508,8 +508,7 @@
 
     { 0x90, 2540, 2540, &usbTabletPC   }, /* TabletPC 0x90 */ 
     { 0x93, 2540, 2540, &usbTabletPC   }, /* TabletPC 0x93 */
-    { 0x9A, 2540, 2540, &usbTabletPC   },  /* TabletPC 0x9A */
-    { 0x32, 2032, 2032, &usbGraphire4  } /* Waltop Slim */
+    { 0x9A, 2540, 2540, &usbTabletPC   }  /* TabletPC 0x9A */
 };
 
 Bool usbWcmInit(LocalDevicePtr local, char* id, float *version)
@@ -528,7 +527,7 @@
     ioctl(local->fd, EVIOCGNAME(sizeof(id)), id);
 
     /* vendor is wacom */
-    if (sID[1] == 0x056A || sID[1] == 0x172f)
+    if (sID[1] == 0x056A)
     {
         common->tablet_id = sID[2];
 
@@ -551,7 +550,7 @@
             common->wcmCapacityDefault = -1; 
         }
 
-        if (common->tablet_id == 0x9A || common->tablet_id == 0x93 || common->tablet_id == 0x90 || common->tablet_id==1)
+        if (common->tablet_id == 0x9A || common->tablet_id == 0x93 || common->tablet_id == 0x90)
         {
             if (common->tablet_id != 0x90)
             {

```
If it's wrong... well... *sigh* I give up.

---

### Post by Favux on 2009-11-04
Hi tudor117,

Also since your resolution is 1024 we probably want to change the line to:
```
+    { 0x32, 1023, 1023, &usbGraphire4  } /* Waltop Slim */

```

No big deal.  It's only a couple of lines to edit after all.  You can just post a modified wcmUSB.c too, since it's not that big.  That's what I was thinking of doing.

---

### Post by tudor117 on 2009-11-04
Hi Favux,

Fair enough I recompiled it like that. Though I don't see much of any difference :P
Just out of interest, why is it 1023 and not 1024?

Added compressed file.

---

### Post by Favux on 2009-11-04
Hi tudor117,

I actually do not know.  It's just when I've seen X complain about it being beyond max value or whatever that's what seems to work.  I think I knew at one time but nothing is coming to me right now.  But since the larger value worked and we don't know the resolution of other Waltop tablets maybe we should have left well enough alone.  Hey, but it worked!

Cool, with the compressed wcmUSB.c we're all set!

---

### Post by oberonking on 2009-11-04
I'm a little lost.... please explain all in one post.

what driver has to download? the stable or development?
I have to do what with wcmUSB.c???

Sorry, but i'm lost 

By the way.... thanks

---

### Post by Favux on 2009-11-04
Hi oberonking,

I think we're using linuxwacom 0.8.4-3 and compiling it using this [HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  At step 4 after you've untarred linuxwacom stop.  Back up the original wcmUSB.c by renaming it to say wcmUSB.c.bak and substitute tudor117's.  Then continue on with the HOW TO.  The wcmUSB.c is located at "linuxwacom-0.8.4-3/src/xdrv/wcmUSB.c".  When you're done make sure you have the "waltop" .fdi in place and you should be good.

---

### Post by tudor117 on 2009-11-04
Hi Favux,

It might not be necessary to install the kernel module.

---

### Post by oberonking on 2009-11-04
ok... thanks to both
I'll try it... hope that work for my

---

### Post by oberonking on 2009-11-04
Guys..... you are the best........
work... same issue like I have in Jaunty (only 2 buttons map and haven't got pressure on Blender)
Thanks!!!!!! many many many of it

PS: My tablet is a Genius G-Pen F509.

---

### Post by Favux on 2009-11-05
Hi oberonking,

Great!  Glad it's working.

Let's look at your "xinput --list" and your Xorg.0.log and see if we can figure out why you don't have pressure in Blender.  Which tudor117 does have.

---

### Post by oberonking on 2009-11-05
> **Favux said:**
> Hi oberonking,

Great!  Glad it's working.

Let's look at your "xinput --list" and your Xorg.0.log and see if we can figure out why you don't have pressure in Blender.  Which tudor117 does have.

Hi guys... don't know why not work for my...
Tablet are take as "stylus" but blender don't have pressure at all

Here you are xinput and xorg's log.

Thanks in advance.

---

### Post by Favux on 2009-11-05
Hi oberonking,

Well your model looks different.

Do you know the resolution of the tablet?  The active area in inches?  The pressure levels?

Let's try something simple first.  I've added the pressure curve option to the .fdi and made it a little softer.  See if that shows pressure in Blender.  You only need to add the pressure line to your waltop .fdi.

>                Option "PressCurve" "x1,y1,x2,y2"
                   sets pressure curve by control  points  x1, y1, x2, and y2.
                   Their values are in range from 0..100. The input for 

                         linear curve (default) is "0,0,100,100";
                         slightly depressed curve (firmer) might be "5,0,100,95";
                         slightly raised curve (softer) might be "0,5,95,100".



---

### Post by oberonking on 2009-11-05
this is my fdi....
I'm gone to try your pressure curve option.

Specifications of my tablet (from the genius page)

Active area 	8.75&#8221; x 5.25&#8221;
Resolution 	2,000 lpi
Report rate 	125 rps
Pen pressure 	1,024 levels
Reading high Max 	10 mm
Macro keys 	26

Attach: This is how my tablet is

---

### Post by oberonking on 2009-11-05
Well... I try with pressure curve option and still not have pressure.

---

### Post by Favux on 2009-11-05
Hi oberonking,

Shoot.  Why couldn't it be easy?

Remind me.  You have pressure in Gimp and elsewhere, right?  Just not Blender.

Did anyone at the Blender forum answer your post about pressure?

---

### Post by oberonking on 2009-11-05
> **Favux said:**
> Hi oberonking,

Shoot.  Why couldn't it be easy?

Remind me.  You have pressure in Gimp and elsewhere, right?  Just not Blender.

Did anyone at the Blender forum answer your post about pressure?

Yes, pressure is ok on every other aplication....
No.. nobody answered me on Blender forum.

---

### Post by Favux on 2009-11-05
Hi oberonking,

And you already tried reinstalling Blender.  We are back to something idiosyncratic with your Ubuntu install.  Did you upgrade to Karmic or do a clean install?  Or somehow you are not configuring Blender correctly.  But since you know how to use it that doesn't seem very likely.

I'll look at what we have.  Don't hold your breath.  It may be days or never before I see anything.

---

### Post by oberonking on 2009-11-05
> **Favux said:**
> Hi oberonking,

And you already tried reinstalling Blender.  We are back to something idiosyncratic with your Ubuntu install.  Did you upgrade to Karmic or do a clean install?  Or somehow you are not configuring Blender correctly.  But since you know how to use it that doesn't seem very likely.

I'll look at what we have.  Don't hold your breath.  It may be days or never before I see anything.

Hi Favux

Karmic: Fresh install.
Blender: Fresh install and resinstall

in windows don't have to change or configure nothin in Blender to have pressure... I think that Blender don't have any option to configure tablets or something like that.

---

### Post by tudor117 on 2009-11-05
Hi guys,

When you say you don't have pressure in Blender, do you mean in sculpt mode?
And how did you install blender?
I just unzipped it and ran it and it just seems to work.

---

### Post by oberonking on 2009-11-05
> **tudor117 said:**
> Hi guys,

When you say you don't have pressure in Blender, do you mean in sculpt mode?
And how did you install blender?
I just unzipped it and ran it and it just seems to work.

Blender instalation: sudo apt-get install blender :P

I download de tar.gz too from Blender's page.

Sculpt and texture paint must have pressure. In windows works both

---

### Post by iBoniek on 2009-11-11
Hi,

I have Pentagram slim tablet which is also recognized as a Waltop slim tablet. I've updated to Karmic x64 and buttons stopped to work. Is there any easy way to fix it? I don't want to mess anything up and it's really hard to get through all this posts.

Thanks in advance.

---

### Post by iBoniek on 2009-11-17
bump

---

### Post by tudor117 on 2009-11-17
Hi iBoniek,

What we did was get the source from [linuxwacom]("http://linuxwacom.sourceforge.net/index.php/dl"). 
Replace the file "wcmUSB.c" with the one provided at post [92.]("http://ubuntuforums.org/showpost.php?p=8244156&postcount=92")
Follow [these instructions]("https://help.ubuntu.com/community/Wacom/LatestDriver") to compile.
It should work if you just simply do 
```
./configure --prefix=/usr
```If that doesn't work, compile the kernel module as well.
Don't forget to modify your fdi afterwards.

EDIT: if you want to get rid of the changes, just re-install "wacom-tools" and "xserver-xorg-input-wacom". You might as well leave them installed as they shouldn't do any bad.

---

### Post by iBoniek on 2009-11-19
And how looks your fdi?

---

### Post by tudor117 on 2009-11-19
Hi iBoniek,

A better question is what's *yours* like?
What did you do before to make your tablet work?
The wacom fdi is located at "*/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi*"
My fdi looks like this:
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="WALTOP">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by iBoniek on 2009-11-21
Mine fdi was empty, but thanks to your advice I finally get my tablet working

---

### Post by jaydubyasee on 2009-11-22
So many thanks.  I've finally managed to get my Aiptek 600U slim tablet working in Karmic.

---

### Post by richard270384 on 2009-11-28
Just for the record, in case anybody else is looking for this info.

This mostly worked for me with the Medion P82012 Design USB Graphics Pad from Aldi in Australia on an Ubuntu 9.1 fresh install. My graphics pad appears to be a rebranded Waltop - [http://www.waltop.com/productDetail.asp?id=21](http://www.waltop.com/productDetail.asp?id=21)

The only problems I have after following the instructions in this thread are pressure sensitivity doesn't seem to be working, and when the graphic pad is disconnected from the USB, Ubuntu seems to exit all programs and log off. 

These aren't major issues for me, but if I find any solutions I'll share them here.

---

### Post by ashwyn on 2010-01-06
Hi Richard,

Just thought I'd mention that I am also using an Aldi's graphics pad from Australia, and these instructions work fine for me including pressure sensitivity.

Have you configured the programs that you want to use with it (e.g. gimp)  With gimp, you go to Preferences>configure input devices, then change 'stylus' from disabled to screen (window works as well, but the pad is confined to the active window.)  Then set the brush dynamics options in the toolbox.

In other programs I believe it is a similar process, but I have not tried.

Thanks everyone here for your hard work!  It means that I was able to get my tablet working the day after upgrading, and I really appreciate that!
:popcorn:

---

### Post by sweena on 2010-01-16
hi (sorry about my english)
I have a Trust widesreen mini tablet (3x5 in, 1024 pressure), which is also recognized as a Waltop slim tablet. I've done everything you said but it's not working, never done.
i did all the steps: download the last module from linuxwacom
compile whit the wcmUSB.c modified and compiled like that
./configure --enable-wacom --prefix=/usr 
because without --enable-wacon i didn't get the wacom.ko
i copied the wacom.ko into /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
change the linuxwacom.fdi like tudor117 posted

and the X crashes when i plug in the tablet, and when it happens i can't go to shell (ctrl+alt+F1... doesn't work), only reboot the computer without the tablet

i thing something is wrong with the module. 
what info do you need to help me?

---

### Post by tudor117 on 2010-01-16
You most likely compiled the newer linux wacom. 
I didn't mention it but the version I compiled was linuxwacom-0.8.4-3.
Sorry about not stating that earlier.
It doesn't appear to be on the site though...
However, it might be possible that linuxwacom fixed the driver for Waltop... just a possibility? I doubt it.
Stick to the same version I used.

Another question I've got is did you install the ubuntu packages from synaptic. There's wacom-tools and xserver-xorg-input-wacom. Not sure if you need them but I got them installed before compiling and installing my "patch".

Good luck.


EDIT.. I uploaded everything that I used. [**_Here it is_**.]("http://cid-22da660e7f9be118.skydrive.live.com/self.aspx/Tablet/linuxwacom-0.8.4-3.tar.bz2") 
It's on my skydrive. I configured it for my own computer and I didn't delete the files. Just be aware of that.

---

### Post by sweena on 2010-01-17
well, i already have that packages from sinaptic
I've tried to compile your version, but i couldn't, so, what i did was change your user name in the makefile file, then i could compile but the same happened when i change the tablet's name (Wacom to WALTOP) in the 10-linuxwacom.fdi  file. X crashed
I supose that the kernel module is not ok.
i don't know why, really, i've done everything, i didn't miss any step, i'm sure, 
this is a unpleasant trouble.

---

### Post by tudor117 on 2010-01-17
Did you configure before making my package?
It should have fixed my makefile...

Just out of interest, did you try it in Jaunty? If so did it work?

---

### Post by sweena on 2010-01-18
look this [threat ]("http://art.ubuntuforums.org/showthread.php?t=1326789")
at the end someone says there is a bug
my tablet is 172f vendor ; waltop slim tablet, and I think we have to wait for now
after i do anything my X always crashs if I put WALTOP at fdi files
In jaunty works fine (only with one button but with pressure) with aiptek driver from sources.

---

### Post by edgimar on 2010-01-18
Just for the record, I have compiled the package provided by Tudor in post #120, and everything is working. 
Before doing the following steps, I already had the xserver-xorg-input-wacom and wacom-tools packages installed on my system.

The steps I followed:  first "./configure" (make sure you have xorg-dev package installed...), then "make install" as root.  Then, I added directly after the deviceinfo tag in /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi: 

```
  <device>
      <match key="info.product" contains="WALTOP">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
      </match>
  </device>
```

(removed the match on if0 which was present in post #114).

Plugged in the tablet -- no crashing, pen works, pressure-sensitivity works.  Can plug-in and unplug with no problems.  Very nice.  Thanks for everyone's work...

Also, as a side note, if you want to save settings which you might set using the xsetwacom tool, you can add this as additional <merge key="input.x11_options.SETTING" type="string">VALUE</merge> lines in the fdi file beneath the one that specifies the "Type" setting (e.g. a line where SETTING is TopX, and VALUE is 100, is equivalent to running "xsetwacom set stylus TopX 100" from the shell upon connecting your tablet.)

In case it's of interest, I'm using 32bit Karmic, and here's some info on the device I'm using (after making the above modifications):

'xsetwacom list' output:
```
stylus           stylus
```

relevant 'lsusb' output:
```
...
Bus 003 Device 006: ID 172f:0034
... 
```

relevant  'xinput --list' output:
```

"stylus"	id=10	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 20000
		Resolution is 508
	Axis 1 :
		Min_value is 0
		Max_value is 12500
		Resolution is 508
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1


```

relevant 'lshal' output:
```

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.product = 'Slim Tablet'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial'  (string)
  info.vendor = 'WALTOP International Corp.'  (string)
  linux.device_file = '/dev/bus/usb/003/006'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 4357  (0x1105)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 6  (0x6)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Slim Tablet'  (string)
  usb_device.product_id = 52  (0x34)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'WALTOP International Corp.'  (string)
  usb_device.vendor_id = 5935  (0x172f)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 4357  (0x1105)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 6  (0x6)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 52  (0x34)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'WALTOP International Corp.'  (string)
  usb.vendor_id = 5935  (0x172f)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.mouse', 'input.tablet', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event11'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_172f_34_noserial_if0'  (string)
  input.product = 'WALTOP International Corp. Slim Tablet'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'stylus'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'base'  (string)
  linux.device_file = '/dev/input/event11'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input15/event11'  (string)

```

---

### Post by sweena on 2010-01-18
edgimar, did you change anything in the tudor's package or did you compile like that?
i have a lot of errors making make and make install.

---

### Post by edgimar on 2010-01-18
> **sweena said:**
> edgimar, did you change anything in the tudor's package or did you compile like that?
i have a lot of errors making make and make install.

I compiled it as is.  As I mentioned in my post, it is of course necessary first to run ./configure.  Look at the errors which are being generated -- they will probably tell you what the problem is.  Perhaps you don't have all the library dependencies installed (e.g. the xorg-dev package) which are needed to compile?

Also, I don't know if it matters which version of gcc you have installed, but I had all available versions from synaptic installed (i.e. 4.1, 4.2, 4.3, and 4.4).

---

### Post by tudor117 on 2010-01-18
> **sweena said:**
> look this [threat ]("http://art.ubuntuforums.org/showthread.php?t=1326789")
my tablet is 172f vendor ; waltop slim tablet, and I think we have to wait for now.

The patch that was made in this thread is specifically supposed to make the tablets with "172f" to work.

As for Sweena, post any errors from configure and make and we'll try to help you.

---

### Post by sweena on 2010-01-18
well, i've tried to compile again the package provided from tudor.
look the files attached

---

### Post by edgimar on 2010-01-19
> **sweena said:**
> well, i've tried to compile again the package provided from tudor.
look the files attached
Below is a diff between my "./configure" output and your "./configure --prefix=/usr" output.  A summary of the differences are:
[LIST]
[*]you're using mawk instead of gawk
[*]you have HAL headers installed
[*]you're using kernel 2.6.31-17 (I'm using 2.6.31-18 )
[*]you have tk/tcl headers installed
[*]you have libwacomxi headers installed
[/LIST]

The diff file:
```
--- configure.txt.edgimar	2010-01-19 15:13:05.000000000 +0100
+++ configure.txt.sweena	2010-01-18 22:57:37.000000000 +0100
@@ -1 +1,2 @@
+sweena@toshio:~/Escritorio/linuxwacom-0.8.4-3$ ./configure --prefix=/usr
 checking for a BSD-compatible install... /usr/bin/install -c
@@ -3,3 +4,4 @@
 checking for a thread-safe mkdir -p... /bin/mkdir -p
-checking for gawk... gawk
+checking for gawk... no
+checking for mawk... mawk
 checking whether make sets $(MAKE)... yes
@@ -17,3 +19,3 @@
 checking dependency style of gcc... gcc3
-checking for gawk... (cached) gawk
+checking for gawk... (cached) mawk
 checking build system type... i686-pc-linux-gnu
@@ -109,3 +111,3 @@
 checking pkg-config is at least version 0.9.0... yes
-checking for HAL... no
+checking for HAL... yes
 checking for arch type... i486-linux-gnu
@@ -113,4 +115,4 @@
 checking for linux-based kernel... yes
-checking for kernel source/headers... /lib/modules/2.6.31-18-generic/build
-checking kernel version... 2.6.31-18-generic
+checking for kernel source/headers... /lib/modules/2.6.31-17-generic/build
+checking kernel version... 2.6.31-17-generic
 checking for kernel module support... yes
@@ -134,14 +136,4 @@
 checking for tcl version... 8.4
-checking for tcl header files... ***
-*** The tcl development environment can not be found.
-*** The header file tcl.h does not appear at the normal
-*** (or provided) include path. Some build features
-*** will be unavailable.
-***
-checking for tk header files... ***
-*** The tk development environment can not be found.
-*** The header file tk.h does not appear at the normal
-*** (or provided) include path. Some build features
-*** will be unavailable.
-***
+checking for tcl header files... found, /usr/include/tcl8.4
+checking for tk header files... found, /usr/include/tcl8.4
 checking ncurses.h usability... yes
@@ -150,3 +142,4 @@
 checking if libwacomcfg should/can be built... yes
-checking if libwacomxi should/can be built... checking if wacdump should/can be built... yes
+checking if libwacomxi should/can be built... yes
+checking if wacdump should/can be built... yes
 checking if xidump should/can be built... yes
@@ -195,3 +188,3 @@
   module versioning - no 
-      kernel source - yes /lib/modules/2.6.31-18-generic/build
+      kernel source - yes /lib/modules/2.6.31-17-generic/build
      XFree86 source - no 
@@ -202,4 +195,4 @@
          xf86config - no
-                TCL - no 
-                 TK - no 
+                TCL - yes /usr/include/tcl8.4
+                 TK - yes /usr/include/tcl8.4
             ncurses - yes
@@ -211,3 +204,3 @@
         libwacomcfg - yes
-         libwacomxi - no
+         libwacomxi - yes
           xsetwacom - yes
@@ -216,3 +209,4 @@
         wacom_drv.o - no
-  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins
+  wacom*_drv quirks - hal Uninit-called IsXExtensionPointer key-events dixScreenOrigins
 ----------------------------------------
+

```

---

### Post by tudor117 on 2010-01-19
I noticed that while running make, there are a bunch of architecture related errors!?!? I ran my build on a 64bit system so it may be my files?
```

/usr/bin/ld: i386:x86-64 architecture of input file `xf86Wacom.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `wcmSerial.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `wcmUSB.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `wcmISDV4.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `wcmXCommand.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `wcmCommon.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `wcmCompat.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `wcmConfig.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `wcmFilter.o' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `wcmTilt2Rotation.o' is incompatible with i386 output
```
Either way, I will try to see if I can use the newer linuxwacom sources to fix the issue. I'll try to do that soon. May take a few weeks as I have my exams for school coming up :S

---

### Post by Favux on 2010-01-19
Hi sweena,

I was thinking it was a 32-bit 64-bit conflict too.  To see which you have:
```
uname -a
or
uname -m
```
I'm suspecting 32-bit.

---

### Post by sweena on 2010-01-20
sweena@toshio:~$ uname -a
Linux toshio 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
sweena@toshio:~$ uname -m
i686

---

### Post by edgimar on 2010-01-20
By the way, do any of you know how to force the wacom X.org module to reload without having to restart X?  I have noticed that if I make changes to the source, and compile/install it, changes only take effect after X is restarted (despite X.org log messages like "UnloadModule" when unplugging/reconnecting the tablet), which makes the testing cycle rather slow and unpleasant.

---

### Post by Favux on 2010-01-20
Hi sweena,

OK, you have a 32-bit install, if it was 64-bit you'd see something like 'x86_64'.  Tudor117 has a 64-bit install.  Since there isn't a precompiled wacom.ko, just the source code, you should be OK.

I think what's hanging you up is the linuxwacom tar has Tudor117's config information in it.  In the config.log I see build_cpu='x86_64'.  And the Makefile has:
```
build_triplet = x86_64-unknown-linux-gnu
host_triplet = x86_64-unknown-linux-gnu
```
So before you run configure do these two commands:
```
make clean
make distclean
```
I think that will fix it for you.

If that doesn't work I suppose another possibility is that the hid-ids.h is 64-bit so get your own:
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
```
and copy it into place:
```
sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
```
I don't think the hid-ids.h in /src/2.6.31 will interfere.


Hi edgimar,

First rebuild all the module dependencies:
```
sudo depmod -a
```
To uninstall the module:
```
sudo modprobe -r wacom
```
And to install it:
```
sudo modprobe wacom
```
That should work but experience has shown the most reliable way is to reboot, with restarting X second.  I don't know why.

---

### Post by edgimar on 2010-01-21
What is not clear to me is how the kernel module "wacom" which is loaded/unloaded with modprobe relates to the X.org module which is loaded by X?  I am only changing the source code of the X.org module, and my tablet works (with tudor's code; except for both side buttons of the pen being mapped to button 2) even when there is no kernel module loaded (i.e. lsmod|grep wacom returns nothing) -- also, my kernel is configured with the Ubuntu defaults, where wacom support is compiled as a module.

So, I'm not sure how unloading and reloading the kernel module will help me, since I want only to be able to change the X.org module, and force the newly compiled module to be used by X without needing to restart X.

---

### Post by Favux on 2010-01-21
Hi edgimar,

> and my tablet works (with tudor's code; except for both side buttons of the pen being mapped to button 2) even when there is no kernel module loaded (i.e. lsmod|grep wacom returns nothing) -- also, my kernel is configured with the Ubuntu defaults, where wacom support is compiled as a module.
Then you are not using tudor117's code.  He patches wcmUSB.c, which is used to "make" wacom.ko (the usb kernel driver/module), to "trick" it into accepting Waltop as a valid Wacom tablet so the Wacom drivers can be used.  The wacom.ko that comes default will reject the Waltop tablet as it does not have a Wacom Vendor or Product ID.

I think if you check Xorg.0.log in /var/log/ (or 'xinput list' or lshal) you'll find another driver, probably a touchpad/mouse driver/.fdi (maybe Synaptic or evdev) has your tablet.

---

### Post by edgimar on 2010-01-21
> **Favux said:**
> 
Then you are not using tudor117's code.  He patches wcmUSB.c, which is used to "make" wacom.ko (the usb kernel driver/module), to "trick" it into 
wcmUSB.c is in the xdrv directory, and when I compile with make, the wacom_drv.so module is built, and is installed in /usr/lib/xorg/modules/input.  I know this because I can delete the file, and after making, it is there again.  If, however, I remove wacom.ko from /lib/modules/2.6.31-17-generic/kernel/drivers/input, then wacom.ko is not replaced after building/installing.

Secondly, if I change one of the debug messages in wcmUSB.c, run 'make install', and then search for the change via 'strings /usr/lib/xorg/modules/input/wacom_drv.so', it is there.

---

### Post by Favux on 2010-01-21
You are correct but it (wcmUSB.c) is handling the raw data wacom.ko translates into system data and sends to Xinput/Xserver where XFree86's Wacom X driver (wacom_drv.o) takes control.  A wacom.ko will be built if you use the ' --enable-wacom' flag with configure:
```
./configure --enable-wacom --prefix=/usr
```
To copy it into place:
```
sudo cp ./src/2.6.31/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```
It is not automatically installed by the makefile.

---

### Post by tudor117 on 2010-01-21
Hmm.. This isn't really relevant to what's happening now. But, I looked at the code from the newest linuxwacom source. It's identical for wcmUSB.c. So, there shouldn't be any problem compiling their package with my version of wcmUSB.c

---

### Post by edgimar on 2010-01-23
> **Favux said:**
> You are correct but it (wcmUSB.c) is handling the raw data wacom.ko translates into system data and sends to Xinput/Xserver where XFree86's Wacom X driver (wacom_drv.o) takes control.

But if wacom.ko is needed (i.e. must be loaded by the kernel) for things to work, why is it that when my tablet is functioning, 'lsmod |grep wacom' yields nothing (i.e. wacom.ko is not loaded)?

---

### Post by Favux on 2010-01-23
Hi edgimar,

Wacom.ko is needed for a usb Wacom tablet, but not a serial or I suppose bluetooth tablet.  So since you have a usb tablet (I think) then I don't see how the linuxwacom drivers can be running your tablet.  Did you check lshal and Xorg.0.log in /var/log like I mentioned in post #136?  That might tell you what has your tablet.  If it's linuxwacom I'm prepared to be amazed.  It would be fun trying to figure out how that's possible.  Another usb kernel module?  Or something in the usb hid section of the kernel?

---

### Post by edgimar on 2010-01-24
> **Favux said:**
> Hi edgimar,
Did you check lshal and Xorg.0.log in /var/log like I mentioned in post #136?  That might tell you what has your tablet.

Based on the lshal output (which is in post #124), it seems that the built-in (CONFIG_USB=y) kernel 'usb' driver is being used directly, as well as usbhid.

---

### Post by FinnFox on 2010-01-30
Hi everybody,

I've got a "Medion MD85637", which is the same like the "Waltop Slim tablet", and thanks to you guys I've got it running and it's working great. :D
A big thanks to everyone who helped to solve it.
You great! Thank you very,very much!

---

### Post by keevee09 on 2010-03-29
>>  +1  <<

I had to read from start to finish through the posts to understand the 'solved' steps in order, including following up on the compiling link but the logic and clearness of your (your=Favux+tudor117 + edgimar) thinking, your perseverance and focus made all the difference. My Aiptek 600U works in Inkscape, Gimp and Blender. (Albeit with only one stylus button function but I find them awkward to use anyway - the price was right but 'long after the price is forgotten, quality will be remembered' as the Wacom elite might quote ;).

Thank you, thank you, thank you!

---

### Post by javabean420 on 2010-04-14
this tutorial really help me get my brand new genius g-pen f610 (i think its the one that started this thread) and now it "works"....... i have to do the quotes cause i have never used a "tablet" interface before so i am learning what i can do with it..... i don't suppose you happen to know about the "magic buttons"(officially referred to as hot keys)... i can think of lots of things to use them for if i can get the "mapping" figured out

---

### Post by tudor117 on 2010-04-15
Hey all,
So I think I found out why the buttons don't work. But I have NO IDEA how to fix them.
If you look at your xorg log, it lists the tablet as "*USB PL/Cintiq*" which is NOT what we wanted it to be (from the source code) which should have been *Graphire4*.

---

### Post by Favux on 2010-04-15
Hi tudor117,

Hmmm.  We'd have to review what we "patched" and try something a little different.  You might have to recompile several times before we got lucky.

If we do get lucky I should be able to make a patch.

---

### Post by tudor117 on 2010-04-15
Hi Favux,
I found something very weird. If I recompile with a regular configure and location usr, *no wacom*, the changes I make don't apply. Previously, it used to work.
Anyways, if I have to compile the kernel module, that means I need to reboot every time I want to test something. It would take a LONG time.
Anyways, what should we try?
I would try removing all the models (WacomModelDesc) that there are except for the one we added. However I never compiled the kernel module so it would take some time.

---

### Post by Favux on 2010-04-15
Hi tudor117,

Naw, it doesn't take that long.  Using my [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") it only takes me 5-10 minutes.  I've learned a tiny bit more since we last tackled it.  Let me review what we did and I'll have something in a day or two, hopefully.

By the way we finally figured out how to compile the linux Waltop driver from the Waltop site and it seems to work.  The driver seems to be based on, a cut down, linuxwacom.

---

### Post by oberonking on 2010-04-15
> **Favux said:**
> Hi tudor117,

Naw, it doesn't take that long.  Using my [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") it only takes me 5-10 minutes.  I've learned a tiny bit more since we last tackled it.  Let me review what we did and I'll have something in a day or two, hopefully.

By the way we finally figured out how to compile the linux Waltop driver from the Waltop site and it seems to work.  The driver seems to be based on, a cut down, linuxwacom.

Hi guys.....
I have Waltop driver compiled and working, using the readme provided with waltop driver.
On Karmic compile and work fine... Lucid nothing seems to work.
neither of booth drivers compiled on lucid, and xserver-xorg-input-wacom not work at all.

---

### Post by Favux on 2010-04-15
Hi oberonking,

Sounds like the Waltop driver hasn't been updated for Xserver 1.7 (the one in Lucid).  Lucid doesn't use the linuxwacom driver, it has switched to xf86-input-wacom for 1.7.  But a patch we get working for linuxwacom should work on it too.

---

### Post by tudor117 on 2010-04-15
Hi guys,

I guess I'll try the Waltop drivers. Just got a question, would I have to recompile every kernel update? Same question goes for if I compile the kernel module with linuxwacom.
Anyhow, thanks guys :)

---

### Post by Favux on 2010-04-15
I forget if a usb kernel driver is built, so I'm not sure.

The thread we got it to compile:  [http://ubuntuforums.org/showthread.php?t=1326789](http://ubuntuforums.org/showthread.php?t=1326789)  See post #23 by jianboli.

---

### Post by tudor117 on 2010-04-16
Thanks Favux, I'll give it a try.

---

### Post by richard270384 on 2010-05-03
Just thought I'd mention that my graphic tablet worked 'out-of-the-box' on a fresh install of 10.04...

Just plugged it in and I was good to go. 

On 9.04/9.10 I could never get the pressure sensitivity to work in GIMP, but that works now as well.

---

### Post by javabean420 on 2010-05-04
do you think the instructions [http://ubuntuforums.org/showthread.php?t=1458678](http://ubuntuforums.org/showthread.php?t=1458678) here would help with functionality for us here in lucid??? that article is "HOWTO Wacom bamboo CTL-460 in Lucid Lynx" but just redoes the whole linuxwacom drivers for that "new" device

---

### Post by Favux on 2010-05-04
Hi javabean420,

I doubt it.  What you need is a waltop.ko, a usb kernel driver/module, that works in Lucid.  Once you have that you can configure the 10-wacom.conf use the wacom X driver, xf86-input-wacom, for the Waltop.

The other option would be to try and hack the wacom kernel driver wacom.ko so the Waltop could use that.  Sort of like we did for wcmUSB.c in Karmic.

We're looking at it in the last few pages on this thread:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  We probably should be posting either on this thread of the Waltop driver compile thread.  Or maybe start a new one?

With Ayuthia helping we have a chance.  He was the coder who started building the driver code for the Bamboo P&T's (setup you linked to) and got the pen, eraser, touch and pad working on them.

---

### Post by javabean420 on 2010-05-05
Sigh..... i know i screwed up

followed the directions(i think) and did the git clone like it said but..... i got 2 different setups linuxwacom-0.8.4-3 and xf86-input-wacom
linuxwacom refused to compile(note it doesn't have 2.6.30 folder) and xf86-* compiled but no wacom.ko bunch of *.lo files though


Edit: Please note my setup(Xubuntu 10.04) my Genius Gpen f610 worked out of the box about.  so long as i didn't try to use it outside of mypaint or gimp.  if i did it tried selecting everything.  in mypaint i couldn't just push one of the buttons on the pen to "click and drag" the canvas..... minor details IMHO but still irks me

---

### Post by Regel on 2010-05-16
I can't seem to get this to work in Lucid. In Karmic things worked eventually after hours of configuration, but now nothing seems to work. I have a Waltop tablet which I have added to the allowed list on wacom driver. The driver compiled and I copied wacom.ko to where it's supposed to go. I put 'wacom' in /etc/modules and it loads up as X starts.

Now, the question is, how do I make ubuntu to use my newly installed wacom driver with my Waltop/Aiptek tablet? I remember doing it via Hal in Karmic, but this seems the wrong way to go in Lucid.

In /dev there are 2 paths to waltop:
```

/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-mouse
and
/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-mouse

```

Dmesg reports on the tablet as follows
```

[  622.123959] input: WALTOP International Corp. Slim Tablet as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input7
[  622.125420] generic-usb 0003:172F:0034.0003: input,hidraw1: USB HID v1.10 Mouse [WALTOP International Corp. Slim Tablet] on usb-0000:00:1d.2-2/input0

```

xinput -list says
```
xinput -list
&#8627; WALTOP International Corp. Slim Tablet  	id=9	[slave  pointer  (2)]
```

I haven't tweaked xorg.conf yet as I don't know how to tweak it.

---

### Post by AlexDS on 2010-07-11
> **Regel said:**
> I can't seem to get this to work in Lucid. In Karmic things worked eventually after hours of configuration, but now nothing seems to work. I have a Waltop tablet which I have added to the allowed list on wacom driver. The driver compiled and I copied wacom.ko to where it's supposed to go. I put 'wacom' in /etc/modules and it loads up as X starts.

Now, the question is, how do I make ubuntu to use my newly installed wacom driver with my Waltop/Aiptek tablet? I remember doing it via Hal in Karmic, but this seems the wrong way to go in Lucid.

In /dev there are 2 paths to waltop:
```

/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-mouse
and
/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-mouse

```Dmesg reports on the tablet as follows
```

[  622.123959] input: WALTOP International Corp. Slim Tablet as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input7
[  622.125420] generic-usb 0003:172F:0034.0003: input,hidraw1: USB HID v1.10 Mouse [WALTOP International Corp. Slim Tablet] on usb-0000:00:1d.2-2/input0

```xinput -list says
```
xinput -list
&#8627; WALTOP International Corp. Slim Tablet      id=9    [slave  pointer  (2)]
```I haven't tweaked xorg.conf yet as I don't know how to tweak it.

Here is how i did it. And works fine on my Ubuntu 10.04 64bit [http://ubuntuforums.org/showthread.php?t=1528329](http://ubuntuforums.org/showthread.php?t=1528329)

---

### Post by sogetsu25g on 2010-09-01
hi im about to buy a GPEN F610 and i want to know if it really works fine in ubuntu 10.x, im going to use the tablet in blender so i will like to know if all buttons are working and is all fully working?
thanks

---

### Post by tudor117 on 2010-09-02
Hi sogetsu25g, this post claims it works [http://ubuntuforums.org/showthread.php?t=1528329](http://ubuntuforums.org/showthread.php?t=1528329) but I haven't given it a try yet.
However, I'm doubting that the buttons work correctly.
I'll give it a try and update.

---

### Post by tudor117 on 2010-09-03
It works better than before. However there's a small problem which is that the buttons randomly change functions from time to time.
At the moment, I wouldn't say the tablet is completely usable.

The shortcuts on the side never worked nor do I think anyone is planning on making them work.

Head over to this thread to see how to make it work. 
_[http://ubuntuforums.org/showthread.php?t=1528329](http://ubuntuforums.org/showthread.php?t=1528329)_
And use Favux's config from the [_5th post_]("http://ubuntuforums.org/showpost.php?p=9577067&postcount=5")

---

### Post by fragpe on 2010-09-05
Hi.  
 I was able to make the buttons work using a modified version of the wcmUSB.c from the xf86-input-wacom-0.10.3 drivers. I think the reason the drivers get the buttons confused is because the GPenF610 use two scancodes to represent the TOP position of the side button. The same two codes are also used for both:the PEN_TIP and the BOTTOM position of the side button. 
  If someone if interested I can post the modifications they are a bit messy but it seems to be working OK.
  Also, I was using evtest to see the event stream at it seems that the special keys have to be mapped from the coordinates, the tablet does not provide special scancodes for each.

---

### Post by Favux on 2010-09-05
Hi fragpe,

Love to see your code modifications.  Please post them.

Also very good news on the Waltop kernel driver.  Nikolai Kondrashov is working on the kernel hid stuff for Waltop.  It looks like he might have even posted a sample waltop.ko if I could figure it out.  I'm able to clone his git but I don't see the Waltop driver.  Anyway things are finally happening.  He seems to have figured it mostly out.

---

### Post by fragpe on 2010-09-06
Here is the patch to wcmUSB.c from the xf86-input-wacom-0.10.3. What it does is that it tries to distinguish between the TIP PRESS and the top side button. Again it is not and elegant mod....
**Please remember to backup the original driver** /usr/lib/xorg/modules/input/wacom_drv.so

After compilation wacom_drv.so will be created which can be copied* to /usr/lib/xorg/modules/input/.

***IMPORTANT**. Make sure that Xorg is not currently using the wacom_drv.so before replacing it. This might lockup your X system. 

Also here is my /usr/lib/X11/xorg.conf.d/10-wacom.conf notice the mofidied MatchProduct. 
```
#/usr/lib/X11/xorg.conf.d/10-wacom.conf
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "WALTOP|Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```

Notes:
 1. To apply the patch
   patch wcmUSB.c < wcmUSB.c.patch

---

### Post by fragpe on 2010-09-06
> **Favux said:**
>  Nikolai Kondrashov is working on the kernel hid stuff for Waltop.  It looks like he might have even posted a sample waltop.ko if I could figure it out.  I'm able to clone his git but I don't see the Waltop driver.
Hi Favux,
  Can you please post a link or PM the info for Nikolai's repository?

   Also attached I have attached the CRUDE GPenF610 tester code I wrote. It is basically Vojtech Pavlik's evtest.c tailored to the GPen tablet.

This code will report the buttons correctly and it also tries to map the MACRO areas based on hardcoded coordinates (is very crude).  I named the macro areas by following the Macrokey Manager naming scheme(screenshot included).

   To use this code X should not have wizardpen or wacom drivers in active use.

---

### Post by Favux on 2010-09-06
Hi fragpe,

Here's the link he gave for the repository:  [http://git.kernel.org/pub/scm/linux/kernel/git/jikos/hid.git](http://git.kernel.org/pub/scm/linux/kernel/git/jikos/hid.git)  When I clone it I get some kernel's HID folder but no hid-waltop.c I can find.

Here's a link to the hid-waltop.c and hid-ids.h I think he's using:  [http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commit;h=refs/heads/for-next](http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=commit;h=refs/heads/for-next)  And the hid-waltop.c:  [http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;f=drivers/hid/hid-waltop.c;hb=refs/heads/for-next](http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;f=drivers/hid/hid-waltop.c;hb=refs/heads/for-next)

I've asked him to post a clean copy of his current hid-waltop.c and headers, without the line numbers.

And here's his post thread:  [https://sourceforge.net/mailarchive/forum.php?thread_name=20100905225009.GB10805%40barra.bne.redhat.com&forum_name=linuxwacom-devel](https://sourceforge.net/mailarchive/forum.php?thread_name=20100905225009.GB10805%40barra.bne.redhat.com&forum_name=linuxwacom-devel)

---

### Post by fragpe on 2010-09-06
Hi Favux,
Thanks for the links!! 
Attached is the hid-waltop.c and the header file without the line numbers. :)

---

### Post by Favux on 2010-09-06
Awesome!  How did you do that?

So then to compile the hid-waltop.ko for Lucid we should be able to do something like:
```
sudo apt-get build-dep linux-meta

sudo apt-get build-dep linux-image-$(uname -r)

cd Desktop

apt-get source linux-image-$(uname -r)

cp stuff-hid-waltop/hid-waltop.c linux-2.6.32/drivers/hid/hid-waltop.c

cp stuff-hid-waltop/hid-ids.h linux-2.6.32/drivers/hid/hid-ids.h

cd linux-2.6.32/drivers/hid

sudo make -C /lib/modules/`uname -r`/build M=`pwd` modules

sudo cp hid-waltop.ko /lib/modules/`uname -r`/kernel/drivers/hid/

sudo depmod -a
```
I'm not sure we want to copy the hid-ids.h, since I don't know what kernel that's from and whether it makes a difference.

A patch would only need to add these 4 lines I believe:
```
#define USB_VENDOR_ID_WALTOP				0x172f
#define USB_DEVICE_ID_WALTOP_SLIM_TABLET_5_8_INCH	0x0032
#define USB_DEVICE_ID_WALTOP_MEDIA_TABLET_10_6_INCH	0x0501
#define USB_DEVICE_ID_WALTOP_MEDIA_TABLET_14_1_INCH	0x0500

```

---

### Post by fragpe on 2010-09-06
> **Favux said:**
> Awesome!  How did you do that?

Well to remove the lines I used Open Office Spread Sheet to read the file in FIXED with mode. Then I removed that column with the numbers. 
However after I posted the files I was able to the browse the full git repository, there you can access the files RAW that will let you save the files with no lines.
[http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=tree;f=drivers/hid;hb=refs/heads/for-next](http://git.kernel.org/?p=linux/kernel/git/jikos/hid.git;a=tree;f=drivers/hid;hb=refs/heads/for-next)

---

### Post by Favux on 2010-09-06
> I was able to the browse the full git repository, there you can access the files RAW that will let you save the files with no lines.
[http://git.kernel.org/?p=linux/kerne...heads/for-next](http://git.kernel.org/?p=linux/kerne...heads/for-next)
That's the magic I was asking about.  I must have beat my head against the wall for at least 5 minutes trying to come up with that view and getting no where.  :)

---

### Post by fragpe on 2010-09-06
> **Favux said:**
> That's the magic I was asking about.  I must have beat my head against the wall for at least 5 minutes trying to come up with that view and getting no where.  :)

Yes.. After I did the Open Office thing I said "there had to be link somewhere" then I started to browse the tree and RAW came to view!! :)

What tablet to you have by the way?

---

### Post by Favux on 2010-09-06
I've got a convertible Wacom tablet pc and a Wacom Bamboo Pen and Touch tablet.

---

### Post by Favux on 2010-09-06
Oops!  Nickolai tells me that the hid-waltop.c & hid-ids.h aren't enough.  :o  Apparently other changes are needed.  I'm waiting for him to explain and send them to me.

---

### Post by fragpe on 2010-09-06
> **Favux said:**
> Oops!  Nickolai tells me that the hid-waltop.c & hid-ids.h aren't enough.  :o  Apparently other changes are needed.  I'm waiting for him to explain and send them to me.
Thanks!  I think that other parts of the kernel hid subsystem have to patched in order to get the module to work (some symbol dependencies may be needed etc). I will send Nickolai my dev descriptor and use his tools to see what else can I find about my device.

---

### Post by fragpe on 2010-09-08
> **Favux said:**
> Oops!  Nickolai tells me that the hid-waltop.c & hid-ids.h aren't enough.  :o  Apparently other changes are needed.  I'm waiting for him to explain and send them to me.

You can get the kernel patches from Nickolai's git repository.
I will try his new patch soon.

Also I have been checking the device output using the usbhid-dump. And now I can identify the pads Macro Keys reliably.  I will see if I can put something together to use them. :)

---

### Post by Favux on 2010-09-08
> now I can identify the pads Macro Keys reliably. I will see if I can put something together to use them.
That would be awesome and the first time they ever worked!
> You can get the kernel patches from Nickolai's git repository.
Where is it?  That's my question.  I can get linux-next with his Waltop branch merged (8-19-10) and I found the diff for his Waltop branch merge so I see the changes needed to the other 3 files or so like Make & kconfig.  Where is his git repo and is it more up to date?

---

### Post by fragpe on 2010-09-08
> **Favux said:**
> That would be awesome and the first time they ever worked!
 
What happens with the keys in these devices is that they have to be "calculated" from the coordinates (there is a way :) ).  Since it seems that the hardware does not output the actual keys. Thus a mapping has to be determined for the devices which can be a limitation. The other alternative will be to collect the values for the waltop or similar devices from other users to create the maps.  I have to do some research to see how other devices work.

> **Favux said:**
> 
Where is it?  That's my question.  I can get linux-next with his Waltop branch merged (8-19-10) and I found the diff for his Waltop branch merge so I see the changes needed to the other 3 files or so like Make & kconfig.  Where is his git repo and is it more up to date?

Here is a link to his latest kernel patch.
[http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=vanilla/2.6.36-rc3.patch;hb=HEAD](http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=vanilla/2.6.36-rc3.patch;hb=HEAD)

This patch has to be applied to the vanilla 2.6.36-rc3 kernel. Since I don't have the vanilla kernel in lucid I can't test right away.  

He also mentioned that the Xorg wacom driver and some modifications to the X config have to be done in order to test the driver. I have to ask him for the config mods.

---

### Post by spbnick on 2010-09-19
Guys, if you need any more help with my patches, please don't hesitate to ask here or via e-mail [EMAIL="spbnick@gmail.com"]spbnick@gmail.com[/EMAIL].

Nikolai Kondrashov

---

