---
title: "TC1000 pen not working"
date: 2011-07-18
forum: General Help
---

### Post by linuxlover42 on 2011-07-18
A while ago I started [this thread]("http://ubuntuforums.org/showthread.php?t=1751149") to try and get the pen on my TC1000 working with fpit. I almost got it working but I could not get past the point where touching the pen to the screen would log me out. Closer inspection of the input devices with xinput list gave me 

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)] 
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)] 
&#9116;   &#8627; Jing-Mold USB K/B+Mouse                     id=11    [slave  pointer  (2)] 
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)] 
       &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)] 
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]     
    &#8627; Power Button                                id=9    [slave  keyboard (3)]     
    &#8627; Jing-Mold USB K/B+Mouse                     id=10    [slave  keyboard (3)]     
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)] 
&#8764; TOUCHSCREEN                                 id=6    [floating slave]

```Which shows the touchscreen to be a floating slave when it should in fact be a slave pointer. Reattaching it to the master pointer worked in regular ubuntu but did not fix the problem. I switched to lubuntu in the meantime which works much faster and attempting to reattach the touchscreen gave me an error message stating that it was a bad device. I recently found [this]("http://vencik.byl.cz/TC1000_And_Linux/") which seems to contain another driver specifically for the TC1000 touchscreen named xf86-input-tc1kpen. However, although I have had a decent amount of experience with linux, I have no idea how to install things like this. Can anyone explain to me how to do it or if this will work in lubuntu 11.4.

Thanks

---

### Post by linuxlover42 on 2011-07-18
If anyone can explain to me how to install things like the attachment I would be most grateful. It also seems that it requires something called fpi2002 to work. In the instructions for installing it it says

> **Kernel modules**

   lsmod gives me [this]("http://vencik.hy.cz/tc1000/lsmod.txt") output. 
Note that some of the loaded modules seem unnecessary; I shall play a bit with that... 
   **fpi2002** kernel module was used to provide tablet serial device. It is now obsoleted by David Kuehling's [fpi2002-new.sh]("http://user.cs.tu-berlin.de/%7Edvdkhlng/fpi2002-new.sh") script, thanks David! 
I don't use the kernel module any more, but if you want it for some reason, it may be found [here]("http://staff.xiaoka.com/smoku/stuff/TC1000/fpi2002-0.5.tar.gz") (version 0.5). 
Instead, as a Gentoo user, I've adapted David's fpi2002-new.sh script for Gentoo runscript-based init system: 


[LIST]
[*]Put the [COLOR=Blue][fpi2002 script]("http://vencik.hy.cz/tc1000/etc/init.d/fpi2002")[/COLOR] to /etc/init.d
[*]and its [COLOR=Blue][configuration]("http://vencik.hy.cz/tc1000/etc/conf.d/fpi2002")[/COLOR] to /etc/conf.d
[*]and don't forget to do rc-update fpi2002 add default
[/LIST]
 
If you use other distribution, David's original script may be more appropriate for you (decide for yourself). What extensions would these two files need?

---

### Post by linuxlover42 on 2011-07-18
Ok I figured out how to install source tarballs but I still need the fpi2002. Can anyone help me?

---

### Post by linuxlover42 on 2011-07-20
please forgive me. This does not work and I can see now why it was a bad idea.

---

