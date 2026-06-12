---
title: "System won't power down"
date: 2004-10-25
forum: General Help
---

### Post by iminj on 2004-10-25
When I shut down ubuntu, I get a final line - something like "powering off"; BUT the system doesn't shut down completely. I have to press the power button for 6-8 seconds to finish the job. It's an old Dell Dimension XPS.

I read somewhere that a module called "apm" was a solution. I did sudo modprobe apm, and I put apm into /etc/modules... but it hasn't solved the problem.

Any ideas folks? Thanks.

---

### Post by water on 2004-10-25
i've got the same problem with an siemens lifebook s6120.

the problem came after i apt-get upgraded to 4.10 final.

i'll try a fresh install in a day or to and see if that changes anything...

:water

---

### Post by az on 2004-10-25
I have to add acpi=force to my grub startup.

Add it to the kernel line and see if that helps.

As soon as I am in front of my computer again, I will file a bug report.  If this is not avoidable, perhaps there can be some sort of gui fix to this...

---

### Post by jdong on 2004-10-25
old, did you say... append **acpi=off apm=power-off**.

---

### Post by Geekboy on 2004-10-25
[QUOTE=azz]I have to add acpi=force to my grub startup.[/QUOTE]

I've tried this and it did not work.  Any other suggestions?

---

### Post by gabbman on 2004-10-25
Edit the /boot/grub/menu.1st file by adding acpi=force to the kernel line as follows.

title		Ubuntu, kernel 2.6.8.1-2-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-2-386 root=/dev/hda1 ro single acpi=force
initrd		/boot/initrd.img-2.6.8.1-2-386
savedefault
boot

That's how I got mine to power off on shut down.

---

### Post by LongTooth on 2004-10-26
I did this: sudo gedit /boot/grub/menu.1st. And got an error message: /dev/dsp: No such file or directory. Of course gedit came up but it was blank. Didn't 'save' it when I exited. Any other suggestions? I know I'm close. When I sudo modprobe apm my machine does shut down completely. So what's the answer? Thanks.

---

### Post by jdong on 2004-10-26
Did you try my options? If you have a computer old enough not to support ACPI, you can force ACPI all day with no results ;)


Try **acpi=off apm=power-off** to turn OFF ACPI, then try using APM to power the system off.

The grub menu file is called menu.[l]st, that's L, as in "menu dot list", not 'menu dot first'

---

### Post by az on 2004-10-26
add apm to your /etc/modules

This will load the apm module on boot.

---

### Post by jahLux on 2004-10-27
Azz, pray tell, exactly HOW do you 'add apm to your /etc/modules'.  A step-by-step instruction layout would be useful to all us newbies struggling to love UBUNTU Linux.
Thanks much!

---

### Post by jahLux on 2004-10-27
[QUOTE=gabbman]Edit the /boot/grub/menu.1st file by adding acpi=force to the kernel line as follows.

title		Ubuntu, kernel 2.6.8.1-2-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-2-386 root=/dev/hda1 ro single acpi=force
initrd		/boot/initrd.img-2.6.8.1-2-386
savedefault
boot

That's how I got mine to power off on shut down.[/QUOTE]


Any idea how to make the fix 'stick' beyond the current session?

---

### Post by HungSquirrel on 2004-10-27
Having the flag in your grub config should make it 'stick', because the option will be enabled every time you boot.

---

### Post by iminj on 2004-10-27
Thanks for all the responses ....BUT,  after doing the following, my system still refuses to power off completely. Here's what I did (so far) ...

(1) added 'apm' to /etc/modules. I see 'Advanced Power Management daemon' load during the ubuntu boot up, so I suppose that means apm is in fact loading. 

(2) I added 'acpi=off apm=power-off' to the end of the ubuntu kernel line in /boot/grub/menu.lst. Again, when I boot up, I can see these instructions on the kernel line as it loads.

But ... it doesn't work. Did I do this wrong, or can anyone think of another method?

---

### Post by az on 2004-10-27
Okay.

To add apm to /etc/modules, open it up in a text editor and add the word apm to the bottom.  You need root priveleges to do this, so using gedit from the menu will complain.  You can either open a root terminal and type
nano /etc/modules

(use Control-O) to save the file and Control-X to quit.

You can also just open up a regular terminal and do 
sudo nano /etc/modules

You can also go into the run command option in your menu and run
gksudo gedit
and then open up /etc/modules.

sudo gives you root priveledges on the command line.  Gksudo does this graphically.  Anyway.

While we are on the topic, You can run the command dmesg to see all the kernel messages that are generated at boot.  dmesg > /home/kurn/file
will throw all that into a file named "file" for you to consult.

You may also browse /var/log/messages (or syslog, or whatever else you wanna know)

So look at your dmesg to see what is actually happening to your apm or acpi.  Then go and play around with you bios settings to see if you can enable a dissabled acpi or apm feature.

For example, when I boot my computer and hit delete, I go into the bios menu and can switch my power control from "disable" to "apm" to "acpi" and "apm/acpi".  I then adjust my kernel parameters accordingly.
All boards are not the same, but it you are able to power down from Windows, you should be able to find a way to power does from linux.
On one machine, I needed to switch the ide setting to something like SMART from "auto" for the machine to power down properly.  That was weird, but anyway...

Maybe someone who knows more about computers can one day tell me whay that was....

Good luck!

---

### Post by taygan on 2004-10-27
I finally got mine to work. this way:

sudo modprobe apm
sudo update-modules

but it wouln't stick

editing /boot/grub/menu.lst kernel line
acpi=off apm=on   didn't work
acpi=off apm=power-off   didn't work
acpi=force   worked

good luck

---

### Post by iminj on 2004-10-27
Still not getting anywhere with this. 

I have apm installed in /etc/modules .... and it loads on boot.
I tried the following 4 combinations of commands at the end of the kernel line in /boot/grub/menu.lst:

acpi=off apm=power-off
acpi=force
acpi=force apm=power-off
apm=power-off 

Nothing worked. When I include acpi in the kernel line, I get an error message during the boot sequence: 'ACPI Unable to locate RSDP'. Can anyone shed light on what this means?

I checked my BIOS. It's Dell ver. A09, and it indicates that I have Power Management "Enabled", but I can find no reference to what type of power management system it uses.

Judging by the number of people reading this. and the number of threads pointing to this issue, it seems it's not uncommon. Hopefully it will be addressed by the folks at ubuntu.

Thanks all
iminj

---

### Post by az on 2004-10-27
I would then think that your board supports apm and not acpi.  You should be able to power down... Just don't put anything in your grub boot.  Keep the apm line in /etc/modules.conf

You should also have apmd installed (try dpkg -l | grep apm)


For giggles, try 
sudo apm -s

And tell me what happens.

---

### Post by iminj on 2004-10-27
heh heh ....

OK ,,, I put /boot/grub/menu.lst back to its original state .... no apm or acpi references on the kernel line. Then, I added apmd as you suggested.

When I did 'sudo apm -s" ....... WHAM !!! ... my system instantly went down. The screen went blank, I'm pretty sure the hard drive stopped ... but the system didn't entirely power down. The system fan was still turning.

OK, this demonstrates that my PC is responsive to apm commands. The question is this >> How do I configure it to shut down completely ?

iminj

---

### Post by FLeiXiuS on 2004-10-27
[QUOTE=iminj]heh heh ....

OK ,,, I put /boot/grub/menu.lst back to its original state .... no apm or acpi references on the kernel line. Then, I added apmd as you suggested.

When I did 'sudo apm -s" ....... WHAM !!! ... my system instantly went down. The screen went blank, I'm pretty sure the hard drive stopped ... but the system didn't entirely power down. The system fan was still turning.

OK, this demonstrates that my PC is responsive to apm commands. The question is this >> How do I configure it to shut down completely ?

iminj[/QUOTE]


You could try adding

```
apm
```

to the modules list.  (/etc/modules)

---

### Post by iminj on 2004-10-28
apm IS in /etc/modules. Sorry, I forgot to mention that in my last post.

---

