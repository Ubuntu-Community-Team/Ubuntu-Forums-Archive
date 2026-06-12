---
title: "Alsamixer wont save my changes"
date: 2009-11-04
forum: General Help
---

### Post by Hund on 2009-11-04
I'm running Ubuntu 9.10 with Openbox on my HTPC. Everytime I start my HTPC I have to execute the command **amixer set Front 100% > /dev/null** or open alsamixer and set it to 100%.

I have added the line in the autostart file for Openbox but that doesnt help at all.

Dunno what to do?

---

### Post by mac9416 on 2009-11-04
Howdy, Hund,

> Here is how I did it:

   1. Run 'alsamixer' in the Terminal
   2. Get the settings where you want them and press Esc to exit
   3. Run 'sudo alsactl store 0' in the Terminal
   4. Run 'sudo gedit /etc/rc.local' in the Terminal
   5. Add "/sbin/alsactl restore" to the end of that file and save it
   6. Reboot and test the results!


If you are not familiar with alsamixer, there's some great info here: [https://help.ubuntu.com/community/So...ng%20alsamixer](https://help.ubuntu.com/community/So...ng%20alsamixer)


Source: [http://ubuntuforums.org/showthread.php?t=1313276&highlight=alsamixer](http://ubuntuforums.org/showthread.php?t=1313276&highlight=alsamixer)

Hope that helps!

---

### Post by zzzBrett on 2009-11-04
> **mac9416 said:**
> Howdy, Hund,



Source: [http://ubuntuforums.org/showthread.php?t=1313276&highlight=alsamixer](http://ubuntuforums.org/showthread.php?t=1313276&highlight=alsamixer)

Hope that helps!

Nice to know -- thanks.

---

### Post by Hund on 2009-11-04
> johan@Fjuppen:~$ sudo alsactl store 0
Home directory /home/johan not ours.


Hm? :shock:

---

### Post by mac9416 on 2009-11-04
That happened to me too. I believe you can safely ignore that. Reboot and test it.

---

### Post by Hund on 2009-11-04
Didnt work. :(

---

### Post by mac9416 on 2009-11-04
Hmmmm. Try following the first three steps, then run '/sbin/alsactl restore' by hand. If that works, I am mistaken about the startup script. I use my fluxbox startup script to run that command, so I am not absolutely sure rc.local even works.

---

### Post by Hund on 2009-11-04
It worked fine when I used the autostart file that Openbox uses. Thx for the help!

---

### Post by mac9416 on 2009-11-04
Very glad to help! 

Here is an updated version of my instructions that should work on other desktop environments.

> 1. Run 'alsamixer' in the Terminal.
2. Get the settings where you want them and press Esc to exit.
3. Run 'sudo alsactl store 0' in the Terminal. You may get an error saying "Home directory X not ours." You can safely ignore that.
4. Run gnome-session-properties and click "Add". Put "Alsamixer Restore" into the Name blank, and "/sbin/alsactl restore" into the Command blank. Feel free to add a description if you like.
6. Click "Add" to finish making the startup item and click "Close" to exit gnome-session-properties.
7. Reboot and check the results!

NOTE: You may prefer to use your Window Manager's startup script instead of steps 4-6.

---

### Post by mthmulders on 2009-12-28
Can I add a very short addition to your guide, mac9416?

In case someone has more than one soundcard, and thus runs alsamixer with the ```
-c x
``` argument, the ```
0
``` in the ```
alsactl store
``` command needs to be replaced with ```
x
```.

---

### Post by mac9416 on 2009-12-28
Thanks for the additions, mthmulders!

However, there's actually a better way to fix the muting problem. I've described it here: [http://ubuntuforums.org/showpost.php?p=8342636&postcount=8](http://ubuntuforums.org/showpost.php?p=8342636&postcount=8)

If that way doesn't work, the instructions above (along with mthmulders' additions) are worth a shot.

---

