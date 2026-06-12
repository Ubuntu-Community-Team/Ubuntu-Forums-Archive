---
title: "plymouth problem"
date: 2010-05-03
forum: General Help
---

### Post by christian8287 on 2010-05-03
hi,

when booting my system some splash with "Ubuntu 10.04" is shown with some dots down the text. my problem is that i have kubuntu and want to display the kubuntu splash instead of (i think it is) the defaut splash screen.

When i execute the following command:
```
sudo update-grub
```
i get
```
Searching for splash image ... none found, skipping ...
```

i tried too:
```
16:05:20@~/>sudo update-alternatives --config default.plymouth 
Es gibt nur eine Alternative in Link-Gruppe default.plymouth: /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth
Nichts zu konfigurieren.
```

so kubuntu-logo is intalled and it should be configured correctly as splash screen...

does anyone know whats the problem and how to configure it correctly?

thanks,
christian.

---

### Post by dino99 on 2010-05-03
some info here:

[http://kubuntuforums.net/forums/index.php?topic=3111199.0](http://kubuntuforums.net/forums/index.php?topic=3111199.0)

[http://ppa.launchpad.net/alessandro-ghersi/staging/ubuntu/pool/main/k/kubuntu-default-settings/](http://ppa.launchpad.net/alessandro-ghersi/staging/ubuntu/pool/main/k/kubuntu-default-settings/)

[https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/551290](https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/551290)

---

### Post by christian8287 on 2010-05-03
thank you for your reply!

but i think the solutions in your links are not related to my problem.

i uninstalled plymouth-theme-ubuntu-text now and i am not getting any splash screen. when the computer boots, only text is shown, but no splash screen.

i tried to install plymouth-theme-ubuntu-logo too, but if i activate it with sudo update-alternatives --config default.plymouth it doesn't make any difference.

does anyone know what can be the problem, that no splash screen appears? it's a little bit strange, because it seems to be configured correctly.

regards,
christian.

---

### Post by Cavsfan on 2010-05-03
Maybe you can find info about it on this page (down a little ways)
I have Ubuntu and a very nice 1920 x 1200 splash screen.

_[COLOR=Blue]http://members.iinet.net/~herman546/p20.html[/COLOR]_

---

### Post by christian8287 on 2010-05-04
i didn't find some information about plymouth in the link youve posted.

now i tried to install grub2 instead of grub, but still no success. ive also tried to reinstall all plymouth packages, but nothing helps...

i couldn't find the same problem by googling or forum search. most of the guys have problem with screen resolution or frame buffer, but nobody said, that no splash screen is shown. its a little bit frustrating, tried so many things...

atm i have no splash screen, only text output on the console while booting the system. plymouth seems to make all things more complicated...

---

### Post by Cavsfan on 2010-05-04
You say you were using grub and installed grub2? 

I am not really familiar with Kubuntu, but I doubt grub cares.
If you have grub2 installed this will apply:

You can enter "sudo grub-mkconfig: to display where everything is coming from.
You will see a line for beginning of file and end of file for each file in the mix.

"sudo gedit /etc/default/grub" will display default line (if dual booting), timeout and resolution of your splash screen. And that is all that can be changed there. 
You will see "GRUB_DEFAULT=0" and this counts 0,1,2,3 etc. if you are dual booting.
And you should see GRUB_GFXMODE and mine is set to "GRUB_GFXMODE=1920x1200x32"
The last number 32 is color depth. You can have this be 640x480 all the way up and past what mine is if your monitor supports it.
If you do make any changes, you need to enter "sudo update-grub".

"sudo gedit /etc/grub.d/05_debian_theme"  (this is where the grub picture and text colors are stored)

I had to create the directory /usr/share/images/grub for the grub splash image to  go in.
Your picture and text colors are controlled after the line "# check for usable backgrounds" this is where you put your file name (exactly like the following line w/o quotes).
    "for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/XXXXXXXXXXXX.{png,tga} ; do"

It may not look like that when you look at it, but if you enter the above line where xxxxxxxxx. is your png or tga or jpg  (you would have to add jpg between the brackets if you have jpg).
I was told that jpgs work better, but mine is OK, so I have not needed to change it yet.
Then below that you will see "# set the background if possible" and a little ways below that is where the text colors get set if you have the image.
I use this:
    set color_normal=white/black
    set color_highlight=yellow/black

Make sure you leave black as your second color as that means transparent.
There are other colors mentioned somewhere in the link in my sig.

And it will vary depending on the color of your image. Mine displays white text for normal and yellow for the highlighted line. For my picture that works best for me, but like i say 
it just depends on your picture and tastes. I just used the # to comment out what was there.

After you're done you must run "sudo update-grub" for the changes to take effect and you should see your
splash picture file name displayed or else something did not go right.

Try all of that and see where you are.

---

### Post by Cavsfan on 2010-05-04
If that last post doesn't do what you want I noticed something in the sticky in General Help for lucid bugs and workarounds about [COLOR=DarkRed][COLOR=Black]Bootup/Plymouth.
On page one down a bit.[/COLOR][/COLOR][B][COLOR=DarkRed]
[/COLOR][/B]

---

