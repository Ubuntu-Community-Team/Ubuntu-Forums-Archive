---
title: "Tablet sensitivity not functioning."
date: 2009-09-03
forum: General Help
---

### Post by snew on 2009-09-03
Hello everyone,

My Intuos3 is almost fully functional however, pressure sensitivity does not work.  I tried enabling input devices in GIMP but that didn't seem to do anything.  

I'm running Jaunty and I have created the .fdi file as directed by the guide on the site, but I may have skipped a crucial step...?

I've also tried booting with the tablet plugged in but no go.

---

### Post by Favux on 2009-09-03
Hi snew,

Pressure should work.

Can you tell me what guide at what site?  So I can look at the .fdi.

Does pressure work in Windows?  I ask to rule out a hardware problem like the stylus tip being broken.

It sounds like you already know this but to configure extended input devices in Gimp see near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by snew on 2009-09-03
Thanks for the reply.  Pressure does work in Windows.  And thank you for that link.  Right now, I got pressure working, however it's only on the eraser and the pen side doesn't work at all, but it's progress. :)

I followed the guide here. [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)

I actually used someone else's fdi that they posted.  I can't find the post at the moment but this is what I pasted into my own fdi.  The only thing I altered was switching the pen tip and the double click button because the pen was registering as a right click and the double click was registering as a normal click.  

```

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>

    <!-- Wacom Intuos3 (Stylus) -->
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.Button1" type="string">3</merge>
        <merge key="input.x11_options.Button2" type="string">2</merge>
        <merge key="input.x11_options.Button3" type="string">1</merge>
        <merge key="input.x11_options.Mode" type="string">Absolute</merge>
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
      </match>
    </match>

    <!-- Wacom Intuos3 (Eraser) -->
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.Button1" type="string">1</merge>
        <merge key="input.x11_options.Mode" type="string">Absolute</merge>
      </match>
    </match>

    <!-- Wacom Intuos3 (Mouse) -->
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="cursor">
        <merge key="input.x11_options.Button1" type="string">3</merge>
        <merge key="input.x11_options.Button2" type="string">2</merge>
        <merge key="input.x11_options.Button3" type="string">1</merge>
        <merge key="input.x11_options.Button4" type="string">5</merge>
        <merge key="input.x11_options.Button5" type="string">4</merge>
        <merge key="input.x11_options.Mode" type="string">Relative</merge>
      </match>
    </match>

    <!-- Wacom Intuos3 (ExpressKeys) -->
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="pad">
        <merge key="input.x11_options.Button1" type="string">core key shift</merge>
        <merge key="input.x11_options.Button2" type="string">core key alt</merge>
        <merge key="input.x11_options.Button3" type="string">core key ctrl</merge>
        <merge key="input.x11_options.Button4" type="string">core key space</merge>
        <merge key="input.x11_options.Button5" type="string">core key shift</merge>
        <merge key="input.x11_options.Button6" type="string">core key alt</merge>
        <merge key="input.x11_options.Button7" type="string">core key ctrl</merge>
        <merge key="input.x11_options.Button8" type="string">core key space</merge>
        <merge key="input.x11_options.StripLDn" type="string">5</merge>
        <merge key="input.x11_options.StripLUp" type="string">4</merge>
        <merge key="input.x11_options.StripRDn" type="string">5</merge>
        <merge key="input.x11_options.StripRUp" type="string">4</merge>
      </match>
    </match>

  </device>
</deviceinfo>

```

The settings for the stylus are a bit strange because they have different functions in GIMP from the ones outside of GIMP. (clicking becomes right-click and it's just all over the place, but it's not a huge deal.)

---

### Post by Favux on 2009-09-03
Hi snew,

Progress.

Thank you for posting that .fdi.  The .fdi is one way to do it.  Maybe:
```
       <merge key="input.x11_options.Button1" type="string">1</merge>
        <merge key="input.x11_options.Button2" type="string">3/merge>
        <merge key="input.x11_options.Button3" type="string">3</merge>
```
Would work better.  And you could also try:
```
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
```
What I usually recommend is a .fdi that parses the HAL names into linuxwacom names so that you can use wacomcpl and xsetwacom commands as before to set up.  That's at post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

And I just helped llex_paul set up his Intuous3.  He starts on post #270 here:  [http://ubuntuforums.org/showthread.php?t=967147&highlight=tablet&page=27](http://ubuntuforums.org/showthread.php?t=967147&highlight=tablet&page=27)  and it goes on scattered through the next couple pages.  If you look through the posts what you need should be there.

Up to you.  Hope this helps.

---

### Post by snew on 2009-09-03
I think it's working now.  Thanks very much!  Though one thing: I'm having to hold down button 1 in orderto use the pen tip (button 3?) to draw.  Is that how it was intended and can it be changed so that I can just draw without holding anything?

---

### Post by Favux on 2009-09-03
Hi snew,

You shouldn't have to hold down a button to draw.

Button1 = 1 or stylus tip/left mouse click

Button2 = first stylus button.  2 is middle mouse click, 3 is right mouse click.

Button3 = second stylus button, (or eraser if only one stylus button?).

---

