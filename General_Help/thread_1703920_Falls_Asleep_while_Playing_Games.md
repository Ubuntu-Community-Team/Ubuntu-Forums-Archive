---
title: "Falls Asleep while Playing Games"
date: 2011-03-09
forum: General Help
---

### Post by UnknownDiety on 2011-03-09
Whenever I'm playing games using my gamepad, the OS Falls asleep after a while. As if I were doing nothing.

---

### Post by wojox on 2011-03-09
It falls a sleep or the screen just blanks?

---

### Post by UnknownDiety on 2011-03-09
The screen goes black and requires me to relogin.

(As in the display goes to sleep when inactive for 15 minutes.

---

### Post by UnknownDiety on 2011-03-11
24 Hour Bump

---

### Post by wojox on 2011-03-11
Go into screensaver and untick the boxes in there. Then power management as well. 

Do you use an xorg.conf file?

---

### Post by UnknownDiety on 2011-03-12
> **wojox said:**
> Go into screensaver and untick the boxes in there. Then power management as well. 

Do you use an xorg.conf file?
I'd rather not have to do that everytime I go to play with my gamepad, but I can do that as a **temporary** solution.

I've no idea if I even have an xorg.conf file.

---

### Post by UnknownDiety on 2011-03-13
Bump

---

### Post by wojox on 2011-03-13
Here this will work [‘Caffeine’ – App To Delay Screensaver/Suspend]("http://www.omgubuntu.co.uk/2009/08/%E2%80%98caffeine%E2%80%99-%E2%80%93-app-to-delay-screensaversuspend/")

---

### Post by UnknownDiety on 2011-03-13
> **wojox said:**
> Here this will work [‘Caffeine’ – App To Delay Screensaver/Suspend]("http://www.omgubuntu.co.uk/2009/08/%E2%80%98caffeine%E2%80%99-%E2%80%93-app-to-delay-screensaversuspend/")

Would still only be a temporary solution. Mainly wanting it to recognize when the gamepads being used causing it to stay away. Much like how it recognizes that the keyboard or mouse is being used.

---

### Post by scouser73 on 2011-03-14
Caffeine will sort the screen from going blank, I have it and it works.

---

### Post by UnknownDiety on 2011-03-14
Yes but not the way in which I'm wanting.

Plus the flash stop isn't working for me or either the sites I watch videos on aren't using flash.

---

### Post by wojox on 2011-03-14
What video card/chip do you have?

```
lspci | grep VGA
```

---

### Post by UnknownDiety on 2011-03-17
0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)

---

### Post by UnknownDiety on 2011-03-18
bump

---

### Post by UnknownDiety on 2011-03-20
bump

---

### Post by UnknownDiety on 2011-04-26
> **UnknownDiety said:**
> Whenever I'm playing games using my gamepad, the OS Falls asleep after a while. As if I were doing nothing. (The screensaver cuts on)
Wanting it to recognize when the gamepads being used causing it to stay away. Much like how it recognizes that the keyboard or mouse is being used.

Bump

---

### Post by slooksterpsv on 2011-04-26
What about using a program to emulate the keyboard with the game pad such as Jkey - that way you could assign like the right, left to the right and left arrow keys; technically if that works it'd be like you were pressing left and right which would reset the timer when playing games.

---

### Post by UnknownDiety on 2011-04-29
> **slooksterpsv said:**
> What about using a program to emulate the keyboard with the game pad such as Jkey - that way you could assign like the right, left to the right and left arrow keys; technically if that works it'd be like you were pressing left and right which would reset the timer when playing games.

I'll have to look into this.

Though theres this one game that has it's own default controls for the controller.

So I don't know if that'd conflict or not :S

Would be the best temporary solution though If I can get it to work properly :)

---

### Post by UnknownDiety on 2011-05-03
bump

---

### Post by UnknownDiety on 2011-05-05
bump

---

### Post by r-senior on 2011-05-05
I don't have a solution, but it is interesting that others have the same problems on Windows 7. Which could imply it is a hardware limitation (or a limitation of two operating systems).

[http://answers.microsoft.com/en-us/windows/forum/windows_other-gaming/windows-7-does-not-recognize-gamepad-as-input-so/4ff1f6d7-d78d-44af-a33e-fb8a0edf6952](http://answers.microsoft.com/en-us/windows/forum/windows_other-gaming/windows-7-does-not-recognize-gamepad-as-input-so/4ff1f6d7-d78d-44af-a33e-fb8a0edf6952)

EDIT: Another workaround here:

[http://ubuntuforums.org/showthread.php?t=693800](http://ubuntuforums.org/showthread.php?t=693800)

---

### Post by UnknownDiety on 2011-05-09
> **r-senior said:**
> I don't have a solution, but it is interesting that others have the same problems on Windows 7. Which could imply it is a hardware limitation (or a limitation of two operating systems).

[http://answers.microsoft.com/en-us/windows/forum/windows_other-gaming/windows-7-does-not-recognize-gamepad-as-input-so/4ff1f6d7-d78d-44af-a33e-fb8a0edf6952](http://answers.microsoft.com/en-us/windows/forum/windows_other-gaming/windows-7-does-not-recognize-gamepad-as-input-so/4ff1f6d7-d78d-44af-a33e-fb8a0edf6952)

EDIT: Another workaround here:

[http://ubuntuforums.org/showthread.php?t=693800](http://ubuntuforums.org/showthread.php?t=693800)


Didn't have this issue on Windows 7 (What I came to Ubuntu from lol)

Tried using that before, and it didn't work :(

Thanks though.

---

