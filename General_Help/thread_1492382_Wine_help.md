---
title: "Wine help"
date: 2010-05-24
forum: General Help
---

### Post by mawil1013 on 2010-05-24
Hello,
I have installed Wine, it all seems so easy but I'm not finding the cd in the cd drive.

I got to the point where i (think) was looking in the cd drive for a cd but can't 'see' it.

What am I doing wrong, Wine seems pretty straight forward.:confused:

---

### Post by AcidMoon on 2010-05-24
I only have a little experience with Wine so this may or may not help! 
Are you trying to install from a CD? What I used to do was to insert the CD and when the new window shows up with all the details right click the "setup.exe" file and choose "Open with Wine program loader".
Hope this might help :)

---

### Post by alexan on 2010-05-24
In Ubuntu all your CD are automounted in the /media folder... and wine should autodetect it. If this don't work and you still need the obsolete "X:\ way"


[alt]+f2 > winecfg > [Drivers] > [Add..] > (chose letter) > [browse] > (chose the folder in /media)

---

### Post by mawil1013 on 2010-05-24
> **AcidMoon said:**
> I only have a little experience with Wine so this may or may not help! 
Are you trying to install from a CD? What I used to do was to insert the CD and when the new window shows up with all the details right click the "setup.exe" file and choose "Open with Wine program loader".
Hope this might help :)

I place cd in cd drive, the cd shows up on desktop, I open it and select open with Wine, then i get this message,
"The file '/media/MasterCook 11/setup.exe' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit."

---

### Post by AcidMoon on 2010-05-24
> **mawil1013 said:**
> I place cd in cd drive, the cd shows up on desktop, I open it and select open with Wine, then i get this message,
"The file '/media/MasterCook 11/setup.exe' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit."

Ouch! I've never had that before sorry! I did google-fu and the solution to that is...

 It is just warning you about running unknown programs. You have to  right click->properties->permissions and select execute.

Having done that you should then be able to right click the file again and do the load with wine thing!

---

### Post by mawil1013 on 2010-05-24
> **AcidMoon said:**
> Ouch! I've never had that before sorry! I did google-fu and the solution to that is...

 It is just warning you about running unknown programs. You have to  right click->properties->permissions and select execute.

Having done that you should then be able to right click the file again and do the load with wine thing!


Man I'm getting slammed, I right click on the program icon on desktop, go to permissions and get this message, "The permissions of MasterCook 11 could not be determined" arggg, this is a brand new cd written for XP, Vista and Win7.

---

### Post by mawil1013 on 2010-05-24
> **alexan said:**
> In Ubuntu all your CD are automounted in the /media folder... and wine should autodetect it. If this don't work and you still need the obsolete "X:\ way"


[alt]+f2 > winecfg > [Drivers] > [Add..] > (chose letter) > [browse] > (chose the folder in /media)

Thanks but I'm so new with this and don't 'program' that this doesn't make sense to me. FYI, the version of Wine is 1.1.42

---

### Post by AcidMoon on 2010-05-24
> **mawil1013 said:**
> Man I'm getting slammed, I right click on the program icon on desktop, go to permissions and get this message, "The permissions of MasterCook 11 could not be determined" arggg, this is a brand new cd written for XP, Vista and Win7.

Lol :P Don't give up yet !!

I meant right click on the setup.exe then You have to go ->properties->permissions and select  execute. I think it's a little tick box under permissions.

Once you've done this then right-click the setup.exe file again and try the "open with wine program loader thing"

Good luck!!

---

### Post by mawil1013 on 2010-05-24
> **AcidMoon said:**
> Lol :P Don't give up yet !!

I meant right click on the setup.exe then You have to go ->properties->permissions and select  execute. I think it's a little tick box under permissions.

Once you've done this then right-click the setup.exe file again and try the "open with wine program loader thing"

Good luck!!

Thanks but it won't let my click on it because it is read only and also won't let me modify it to read/write, thanks for your help friend!

---

### Post by AcidMoon on 2010-05-24
> **mawil1013 said:**
> Thanks but it won't let my click on it because it is read only and also won't let me modify it to read/write, thanks for your help friend!

Your welcome friend :) Sorry your having such a nightmare with it!! The tech-guys here will probably solve your problem in 20secs LOL.

Mmm might be worth a random try but maybe eject the CD... put it back in and try those two steps again? I know it sounds dumb but maybe worth a try!

If not I'm sorry but I'm out of ideas #-o

EDIT: Just found this thread which might help: [http://ubuntuforums.org/showthread.php?p=9168666.]("http://ubuntuforums.org/showthread.php?p=9168666")
I think you'd open the terminal, type wine and drag the setup file into the terminal window!

---

### Post by mawil1013 on 2010-05-24
> **alexan said:**
> In Ubuntu all your CD are automounted in the /media folder... and wine should autodetect it. If this don't work and you still need the obsolete "X:\ way"


[alt]+f2 > winecfg > [Drivers] > [Add..] > (chose letter) > [browse] > (chose the folder in /media)

I figured this out and selected D:, i keep getting stopped at wine loader cannot open set.exe because permissions is set to read only and cannot be changed.

---

### Post by AcidMoon on 2010-05-24
> **mawil1013 said:**
> I figured this out and selected D:, i keep getting stopped at wine loader cannot open set.exe because permissions is set to read only and cannot be changed.

Hi. Check out the EDIT on my last post, there's a cool thread I found about your file permission problem.

The idea they say is:
Open a terminal
Type "wine"
Drag the "setup.exe" file into the terminal window.

According to the link it should work :)

---

### Post by mawil1013 on 2010-05-24
> **AcidMoon said:**
> Hi. Check out the EDIT on my last post, there's a cool thread I found about your file permission problem.

The idea they say is:
Open a terminal
Type "wine"
Drag the "setup.exe" file into the terminal window.

According to the link it should work :)

LOL, got ya hooked! Ok, I did alt and f2, which opened terminal block, if i understood you correctly i was to type into the window,, wine then 'drag' the setup.exe into the block,, which i did and c=got same thing about not an exe.

Now that all said, let me tell you that i right clicked on setup.exe and selected, open with A Wine appliction and it installed, well, it does show up in the Wine folder and acts like it's opening but it never does, let me also say that the software install adobe 9 also for MasterCook to work in all it's forms. but I continue to get a message while loading Adobe there is a major issue and it cannot be install, well, I'm about to try installing Reader5 which is supposed to work well and hope that Mastercook will run.

---

### Post by AcidMoon on 2010-05-24
> **mawil1013 said:**
> LOL, got ya hooked! Ok, I did alt and f2, which opened terminal block, if i understood you correctly i was to type into the window,, wine then 'drag' the setup.exe into the block,, which i did and c=got same thing about not an exe.

Heh heh! I think I am hooked - you're right aren't you! :)

Umm well Alt+F2 is like the "run command" in Windows. Terminal is an actual window in itself: You should be able to find it under Applications > Accessories > Terminal.
Check out [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal) if you're unsure. This will load a whole new window (the BASH shell) i meant to type wine in there and then drag the setup.exe file into the window. To be honest I'm not sure whether it would be much different to what you did. Mmm!

However the main thing is that you seem to have got the program installed which is credit to you! The fact it doesn't open is not so un-usual as lots of Win programs have problems in Wine. (Sorry wine devs)

I'm off into compulsive posting rehab for a while hehehe. Good luck with Reader5 friend :)

---

### Post by mawil1013 on 2010-05-24
> **AcidMoon said:**
> Heh heh! I think I am hooked - you're right aren't you! :)

Umm well Alt+F2 is like the "run command" in Windows. Terminal is an actual window in itself: You should be able to find it under Applications > Accessories > Terminal.
Check out [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal) if you're unsure. This will load a whole new window (the BASH shell) i meant to type wine in there and then drag the setup.exe file into the window. To be honest I'm not sure whether it would be much different to what you did. Mmm!

However the main thing is that you seem to have got the program installed which is credit to you! The fact it doesn't open is not so un-usual as lots of Win programs have problems in Wine. (Sorry wine devs)

I'm off into compulsive posting rehab for a while hehehe. Good luck with Reader5 friend :)

coward! Ha, Ha, I'm uninstalling everything now! Starting from scratch then will try this approach, thank you my friend!

---

