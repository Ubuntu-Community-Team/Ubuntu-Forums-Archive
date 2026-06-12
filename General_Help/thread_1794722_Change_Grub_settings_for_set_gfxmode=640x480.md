---
title: "Change Grub settings for set gfxmode=640x480"
date: 2011-07-01
forum: General Help
---

### Post by y3ahright on 2011-07-01
My server showed a black screen on the monitor because the resolution was out of range.  I fixed this problem by pressing 'e' at the grub menu and I changed the first line to say "set gfxmode=640x480"

What do I need to change in my grub settings to make this a permanent change?

Thanks.

---

### Post by drs305 on 2011-07-01
If you can use a GUI, I would expect Grub Customizer can do this. Click on the link in my signature line.

For manual editing, to make the same change you made from the grub prompt:```

gksu gedit /etc/default/grub
*or*
sudo nano /etc/default/grub
```
Uncomment this line and change it to the value you wish to use:
> GRUB_GFXMODE="800x600"

Once you have saved the change, run:
```
sudo update-grub
```

Tip: You can see the resolutions available during boot by going to the grub prompt and typing "vbeinfo".

---

### Post by collisionystm on 2011-07-01
Install Startup-manager from the software Center. You can change the default resolution with a nice GUI.

---

### Post by y3ahright on 2011-07-01
> **drs305 said:**
> If you can use a GUI, I would expect Grub Customizer can do this. Click on the link in my signature line.

For manual editing, to make the same change you made from the grub prompt:```

gksu gedit /etc/default/grub
*or*
sudo nano /etc/default/grub
```
Uncomment this line and change it to the value you wish to use:


Once you have saved the change, run:
```
sudo update-grub
```

Tip: You can see the resolutions available during boot by going to the grub prompt and typing "vbeinfo".

No GUI for me but thank you.  I edited that line to say 640x480, I just was not sure if that was only for the grub menu.

Appreciate it.

---

### Post by drs305 on 2011-07-01
> **y3ahright said:**
>  I just was not sure if that was only for the grub menu.

It is for the grub menu, but G2 continues to improve and now passes some of it's information on to the system. Regardless, if setting the gfxmode in the command prompt did what you wanted it to do when your system boots, this will duplicate that action via the edited file setting.

If you haven't done so and don't seek any further input, please mark the thread 'solved' via the 'Thread Tools' link at the top right of the first post. You can remove the tag from the same place, or just wait to mark it solved when you wish.

---

### Post by y3ahright on 2011-07-01
> **drs305 said:**
> It is for the grub menu, but G2 continues to improve and now passes some of it's information on to the system. Regardless, if setting the gfxmode in the command prompt did what you wanted it to do when your system boots, this will duplicate that action via the edited file setting.

If you haven't done so and don't seek any further input, please mark the thread 'solved' via the 'Thread Tools' link at the top right of the first post. You can remove the tag from the same place, or just wait to mark it solved when you wish.

That did not change the setting.  What I want is for the line in the grub edit menu from grub menu -> 'e' is the 3rd line that says

```
set gfxpayload=$linux_gfx_mode
```

changed to:

```
set gfxmode=640x480
```

---

### Post by drs305 on 2011-07-01
I've edited my two latest posts to combine them.

First, what I've written below is how you would set *linux_gfx_mode* value, which in turn would set the *gfxpayload* setting. This isn't specifically what you asked, but it may be what you want. Explanation later **

The preferred method would be to introduce the variable in /etc/default/grub, since that is the normal file to add or modify Grub2 settings.

I looked at the available settings for /etc/default/grub, and the following appears to be acceptable. Add this line to /etc/default/grub, substituting any compatible value for '640x480'.

> GRUB_GFXPAYLOAD_LINUX="640x480"

Save the file and update-grub.

If you look at the menuentry, the value will still show "linux_gfx_menu", but just above the menuentry you will see that this value has been set to the value you entered in /etc/default/grub. 

A more direct edit, and less preferable, would be to directly edit lines 97-99 (approximately, in Grub 1.99RC) of /etc/grub.d/10_linux:

```
sudo nano /etc/grub.d/10_linux
```
>   cat << EOF
	[s]set gfxpayload=\$linux_gfx_mode[/s]  
        set gfxpayload=800x600
EOF

** Explanation: You asked how to change "set gfxpayload=$linux_gfx_mode" to "set gfxmode=640x480". The "gfxmode" is set in the manner I described in an earlier post (Remove the # symbol from the setting in /etc/default/grub). There is no need to replace the "set gfxpayload" with "set gfxmode=". However, perhaps your problem is with the "gfxpayload" setting itself. If it was causing you problems, replacing it would work, but in reality the reason it might work is simply because you are removing the "gfxpayload" setting, not by substituting the "gfxmode" setting in the same line.

By changing the "gfxpayload" number in the method I described earlier in this post you may solve your problem. If not, if you really want to get rid of the "gfxpayload" variable, just remove it (line 98 or so) by commenting "#	set gfxpayload=\$linux_gfx_mode" it in /etc/grub.d/10_linux and then update-grub

If you get confused by this contorted explanation feel free to ask questions.  ;-)

---

### Post by y3ahright on 2011-07-01
> **drs305 said:**
> Note: See next post if you haven't tried this one already...

To change that line, the direct way is to edit lines 97-99 (approximately, in Grub 1.99RC) of /etc/grub.d/10_linux:



```
sudo nano /etc/grub.d/10_linux
```

I'll take a look and see if I can find an automated way of incorporating it, but for now you can replace the [COLOR="Red"]\$linux_gfx_mode[/COLOR] part with what you want. Save the file, update grub and you should have what you want.

Even if this works, don't mark the thread Solved so that someone else may provide a better way to incorporate the change.

I looked at the available settings for /etc/default/grub, and the following appears to be acceptable. Place a # symbol in front of the line you may have added from the previous post in 10_linux (or correct if you directly edited the line). Then add this line to /etc/default/grub:



Save the file and update-grub.

Background: This should work but it won't show the actual value in the menu entry. It will still display "$linux_gfx_mode" although the value should be the value you use in the entry above. Try it and let me know if it uses the value input below. If not, use the method in the previous post and let me know.

The first one seemed to fix the problem.  The second option (which I tried first) did not fix it.
after I changed: 
```
set gfx_payload=\$linux_gfx_mode
```
to:
```
set gfxmode=640x480
```

and did 

```
sudo update-grub
```

I can now see my screen upon reboots.

Thank you very much!

---

