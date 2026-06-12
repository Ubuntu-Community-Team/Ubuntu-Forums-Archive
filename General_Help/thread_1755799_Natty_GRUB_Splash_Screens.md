---
title: "Natty: GRUB Splash Screens"
date: 2011-05-11
forum: General Help
---

### Post by coljohnhannibalsmith on 2011-05-11
Hello,

I have never had a boot-splash screen on my dual-boot configuration; and I recently added something in Synaptic, probably by mistake, that added a Debian splash screen to my boot menu.  I think it's much more attractive than the bare menu; however it's not appropriate for an Ubuntu distro.  Also, I'd like to know how to add and select boot-splash screens, that will show behind my boot menu, like the Debian screen does.

Can someone tell me how to do this?

[IMG]http://4.bp.blogspot.com/_6bnF8Zv-ZCM/Sp_P0u10FvI/AAAAAAAAALQ/_8EDZOSJTXU/s400/grub2-pretty-menu.png[/IMG]

---

### Post by drs305 on 2011-05-11
Did you add this? It could have been part of the desktop-base (?) package. I thought it was a strange pick as well, but remember Grub is not OS specific.

In any case, there is a very easy way to add a new background: drop an appropriate image file into /boot/grub and "sudo update-grub".

Here is a link to a guide I wrote about this feature:
[http://ubuntuforums.org/showthread.php?t=1739412]("http://ubuntuforums.org/showthread.php?t=1739412")

---

### Post by grahammechanical on 2011-05-11
Oh, I most definitely recommend Grub Customizer. Thanks drs305. This utility should be a standard Ubuntu utility. It should be in System Settings.

Regards.

---

### Post by coljohnhannibalsmith on 2011-05-11
> **drs305 said:**
> Did you add this? It could have been part of the desktop-base (?) package. I thought it was a strange pick as well, but remember Grub is not OS specific.


Yes, it appears, it is a part of the desktop-base, only mine is not in French.  This was a web image I selected to better illustrate the situation.  Since by now, I've learned how to use most of the forum's controls; I've chosen not to limit myself to text-only posts.  I think this is better for everyone.

Also, thanks for the very informative thread.  I've also loaded GRUB Customizer.  The instructions are here:

[http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html)

And I agree with [COLOR=Red]*grahammechanical*[/COLOR] that (sic) *[COLOR=Red]"This utility should be a standard Ubuntu utility. It should be in System Settings;"[/COLOR]* or at least in the repositories.

Actually, I haven't tried it yet; but it looks promising...  I'll make a few attempts with it before I mark this thread as [B][I]solved.

[/I] 
Now, where do I get suitable artwork???
[/B] 



[COLOR=Blue]Hannibal[/COLOR]

---

### Post by drs305 on 2011-05-11
Although I post some information about splash screens, I'm not a huge user of 'eye candy'. I can tell you that there are about 10 standard Grub2 splash images available in the repositories.

You can install them via command line:```

sudo apt-get install grub2-splashimages
```

Once you run the code, they can be found in /usr/share/images/grub/

If you find one you like, you can either copy/move it to /boot/grub, where it will be added as a background automatically (in Natty), or use this setting in /etc/default/grub:
> GRUB_BACKROUND="<path>/<filename>"
Example:
GRUB_BACKGROUND="/usr/share/images/grub/Fly-Angel.tga"

Don't forget to run "sudo update-grub" to add the change to grub.cfg

(There is also a link in my signature line for Grub Customizer installation and usage).

---

### Post by drs305 on 2011-05-12
With the OP's permission, I have moved the discussion of Grub Customizer and background images over to the following thread:
[HOWTO: Grub Customizer]("http://ubuntuforums.org/showpost.php?p=10804027&postcount=108") 
Click on the top right link of the post to view the entire thread.

For continued questions regarding Natty and splash images using methods other than Grub Customizer feel free to continue to post here.

---

### Post by coljohnhannibalsmith on 2011-05-12
Thank you drs305

However, the continuation of the OPs thread starts on page 11:

[http://ubuntuforums.org/showthread.php?t=1664134&page=11](http://ubuntuforums.org/showthread.php?t=1664134&page=11)



OP

---

### Post by drs305 on 2011-05-12
I've updated the link to point specifically to his post. Sometimes the page numbers don't translate depending on the  individual's settings, but it's probably better to do it that way regardless. Others can look for the date. It will show only the specific post, then click the thread link at the top right of the page. 

Or use coljohnhannibalsmith's link to at least take you to the correct page.

 Thanks.

---

