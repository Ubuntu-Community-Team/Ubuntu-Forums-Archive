---
title: "Ubuntu Booting problem"
date: 2011-05-03
forum: General Help
---

### Post by ~G~ on 2011-05-03
Hello, I'm new to Ubuntu (installed on my desktop yesterday). Since this isn't an introduction thread I'll state my problem now.

When I press the power button my computer it loads until it gets to a reddish-black screen and just stays like that forever. So I tried pressing ctrl+alt+delete which then restarts the computer. After loading it gives me the option to start normally, in safe mode, or do a memory test (already tried the memory test). After selecting the (what I think is) "start normally" option, it brings up a command line like screen. It tells me I can type "help" to view the commands I can type, only after typing "help" I type "exit" then it proceeds to load the log in screen. I tried typing exit before help and it doesn't do anything. Now as new as I am to Ubuntu, I'm gonna go out on a limb here and guess that's not how the booting sequence is supposed to work. Help please?

---

### Post by krishnandu.sarkar on 2011-05-03
Well, it's a common problem that we all are facing. Till now we didn't find any actual solution, but diff. solutions are working for each.

A generalized solution would be while selecting Kernel in GRUB menu, press e and add "nomodset" (without quotes) and see if it works.

---

### Post by ~G~ on 2011-05-03
Kernel? I doesn't say the word "kernel" anywhere in the GRUB menu... I pressed e while Ubuntu, with linux was highlighted and typed "nomodset" at the bottom of the page and after pressing F10 I got a red-black screen and it said nomodset was an unknown command or something similar... and I still got sent to BusyBox (but this time "help" then "exit" did nothing).

---

### Post by idoitprone on 2011-05-03
You add it to the end of linux.

nomodeset is a kernel parameter that turn off kms in the kernel. You may have proprietary video driver that is messing with kms causing those black screens. Turning it off will might help with your video issue


```
set root=(hd0,1)
search --no-floppy --fs-uuid --set cb201140-52f8-4449-9a95-749b27b58ce8
linux /boot/vmlinuz-2.6.31-11-generic root=UUID=cb201140-52f8-4449-9a95-749b27b58ce8 ro quiet splash **[SIZE="2"]nomodeset[/SIZE]**
initrd /boot/initrd.img-2.6.31-11-generic
```

---

### Post by ~G~ on 2011-05-07
I placed nomodset at the end of the linux line and pressed F10 and it went to busybox. Typed exit and it went to the logon screen as usual. I turned the computer off then back on and nope, still goes, blinking line>red-black screen. I looked where I placed nomodset and it wasn't there.

Looks like this:
```
ser root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 70efa7a3-5848-47bf-99c4-8d2cf395aba4
linux /boot/vmlinuz-2.6.38-8generic root=UUID=70efa7a3-5848-47bf-99c4-8d2cf395aba4 ro   quiet plach vt.handoff=7
initrd /boot/initrd.img-2.6.38-8-generic
```

---

### Post by wilee-nilee on 2011-05-07
> **~G~ said:**
> I placed nomodset at the end of the linux line and pressed F10 and it went to busybox. Typed exit and it went to the logon screen as usual. I turned the computer off then back on and nope, still goes, blinking line>red-black screen. I looked where I placed nomodset and it wasn't there.

Looks like this:
```
ser root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 70efa7a3-5848-47bf-99c4-8d2cf395aba4
linux /boot/vmlinuz-2.6.38-8generic root=UUID=70efa7a3-5848-47bf-99c4-8d2cf395aba4 ro   quiet plach vt.handoff=7
initrd /boot/initrd.img-2.6.38-8-generic
```

You hit crtl-x after the edit. You get to a cli login ...login in then run startx to get to the desktop.

Look in the menu for additional drivers, and see if there are any.

There is also a failsafe boot in that gui you get from booting the recovery. Just clicking recovery then continue boot does nothing.

---

### Post by ~G~ on 2011-05-08
K picture time.

1)So it goes from this:
[[IMG]http://i1140.photobucket.com/albums/n574/G__/th_103_3115.jpg[/IMG]]("http://s1140.photobucket.com/albums/n574/G__/?action=view&current=103_3115.jpg")
which is my startup screen where it checks for hardware or whatever it's doing , did it when I had windows installed too
2)Then it goes to this:
[[IMG]http://i1140.photobucket.com/albums/n574/G__/th_103_3117.jpg[/IMG]]("http://s1140.photobucket.com/albums/n574/G__/?action=view&current=103_3117.jpg")
Blinking cursor, you'll notice that it is not at the very top for whatever reason.
3)Afterwards this shows up:
[[IMG]http://i1140.photobucket.com/albums/n574/G__/th_103_3120.jpg[/IMG]]("http://s1140.photobucket.com/albums/n574/G__/?action=view&current=103_3120.jpg")
And then it stays here forever until I press Ctrl+Alt+Delete
4)After pressing Ctrl+Alt+Delete, it goes back to 1 then 2 then this shows up:
[[IMG]http://i1140.photobucket.com/albums/n574/G__/th_103_3121.jpg[/IMG]]("http://s1140.photobucket.com/albums/n574/G__/?action=view&current=103_3121.jpg")
I then press enter on the first highlighted option and it then goes to a screen exactly like 3
5)Then:
[[IMG]http://i1140.photobucket.com/albums/n574/G__/th_103_3123.jpg[/IMG]]("http://s1140.photobucket.com/albums/n574/G__/?action=view&current=103_3123.jpg")
Another blinking line, unlike the previous one this one IS at the top of the screen
6)Then it goes to this:
[[IMG]http://i1140.photobucket.com/albums/n574/G__/th_103_3125.jpg[/IMG]]("http://s1140.photobucket.com/albums/n574/G__/?action=view&current=103_3125.jpg")
I type "exit", nothing happens so after typing help, pressing enter:
7)It eventually goes here after some loading:
[[IMG]http://i1140.photobucket.com/albums/n574/G__/th_103_3128.jpg[/IMG]]("http://s1140.photobucket.com/albums/n574/G__/?action=view&current=103_3128.jpg")
8)I log in and my desk top shows up:
[[IMG]http://i1140.photobucket.com/albums/n574/G__/th_103_3129.jpg[/IMG]]("http://s1140.photobucket.com/albums/n574/G__/?action=view&current=103_3129.jpg")


What I would like is a "normal" boot after I press the power button which I would imagine would go something like 1 then2 then 7 then 8. So what do I do?
I would also request that directions be given in plain English, not that secret code tech speak stuff. I'm normally very tech savvy but for whatever reason I have no idea what you all are talking about, so you could use some secret code, just don't go overboard.
Note: All pictures acre click-able thumbnails so if for whatever reason you need to see them larger go ahead and click away.

---

### Post by Quackers on 2011-05-08
If you reboot and then try a normal boot, when the Busybox message comes up that ends with the initramfs prompt, leave it for about 10 seconds then type in exit and press enter key. Does the system then boot?

---

### Post by ~G~ on 2011-05-08
> **Quackers said:**
> If you reboot and then try a normal boot, when the Busybox message comes up that ends with the initramfs prompt, leave it for about 10 seconds then type in exit and press enter key. Does the system then boot?

Yes, after waiting 15 seconds (I added 5 extra seconds just to be safe) it went to the log on screen.

---

