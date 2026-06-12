---
title: "This Is Driving Me Crazy!!!!"
date: 2009-07-26
forum: General Help
---

### Post by cottfcfan on 2009-07-26
Ive mentioned this in many threads, and scoured the web, but found no answers.
 I really need your help.
Ive just installed the ATI 9.7 latest driver for my Radeon HD2400 Driver.
Followed instructions to the letter and reboot. Perfect, no problems.
 Watching the BBC iplayer in Fullscreen, on my system monitor, I see its using 23% CPU on the "operapluginwrapper".

Reeboot and problems start.
 Playing the same program its now using 75% CPU, occasionally maxing out and causing choppy video playback.

I originally blamed Flashplayer, but because of the nature of the problem I now can`t see it being that.

It dosen`t matter what Browser I use, or what Driver I use, the problems always the same.

Can someone please help??

---

### Post by LoneWolfJack on 2009-07-26
it's quite possible the latest driver introduced a new problem. maybe you will want to downgrade the driver to the version you were using before.

---

### Post by cottfcfan on 2009-07-26
Hi..
Ive used the 9.5, 9.6 and now 9.7 driver, plus the one in Hardware Drivers,
the problem is always the same.
The strange thing is, is that if I boot with "acpi=off" added to my kernel, the problem goes away.
But then I lose all my power options, so thats really not an alternative.

---

### Post by cottfcfan on 2009-07-27
Bump... Can anyone help with this problem?

---

### Post by wojox on 2009-07-27
What kernel are you use using:

```
uname -a
```

---

### Post by cottfcfan on 2009-07-27
At the moment im using 2.6.28-13 on jaunty, but ive also tried the .30 kernel and .31rc4, but problem persists.

---

### Post by Taus on 2009-07-27
have you tried to update your bios maybe?

---

### Post by cottfcfan on 2009-07-27
Hi Taus,
Thats an idea, I did update my bios from the Dell website when i was using Vista back in Feb.
 It could be that, that is when my problems started.
I`m going to use the Dell Wiki, Bios and firmware update thats listed on the Forum, and see if it helps.
 Will report back later.

---

### Post by Taus on 2009-07-27
i never had that specific problem but i had tons of gfx related probs with my ati driver. and once i updated the bios everything worked smoothly.

---

### Post by LexMortis on 2009-07-27
I have the same problem, "operapluginwrapper" just eats the CPU alive.
Ive tried the mozilla and the non-free flashplugin, makes no difference. I've tried a few Opera versions (latest stable 9.6x, 10b2 and the latest snapshot).

Youtube is usually fine, but flashgames are not.

Weird thing is... it all runs fine in Firefox, same plugins.
Usually FF does eat up quite a bit of the CPU, but not a single stutter.
As opposed to in Opera, where the wrapper uses more of the CPU but still plays flash dodgy and stutters quite a bit. (flashgames that is, YT is fine)

I dont think its related to Ati / gfx drivers.. seems more of an flashplugin(s) / opera issue. I would love to here from other Opera users and their flash performance + setup/plugins.

Also, how does 9.7 work for you? I recently downgraded from 9.6 to 9.4 because of some dodgy stuff. Is 9.7 proper?

---

### Post by Taus on 2009-07-27
it wasn't my intention to suggest that it could be an ATI gfx driver issue. I apoligize if it's read that way. But i merely just stated that i had tons of bios related problems due to my ATI drivers.

I just thought it could be BIOS related when it works for him when he turns off the power control.

---

### Post by twright on 2009-07-27
This is probably an issue with running flash in a wrapper if I understand correctly as any wrapper around flash is likely to cause severe performance issues. One thing I can suggest though is you try different options for the acpi boot option as it is not only limited to on and off (googling should provide some more info on this). Also are the problems present when using the open source ATI drivers or turning off compiz?

---

### Post by cottfcfan on 2009-07-27
My problems are not just with Opera, but any browser. And I don`t think its just a flash issue as flash works fine with acpi=off.
 If acpi is off, then idling shows my cpu is using between 5-8%.
With acpi on it idles at around 20% which imo is far too much.
 The same problem is with or without ATI Drivers or FGLRX, so i dont think its a driver problem.
 It could be a BIOS problem, but ive just tried updating my BIOS using the instructions from here,

[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

and i cant get anywhere just this in a terminal:

sudo wget -q -O - [http://linux.dell.com/repo/firmware/bootstrap.cgi](http://linux.dell.com/repo/firmware/bootstrap.cgi) | bash
bash: line 230: /etc/apt/sources.list.d/dell-software-temp-bootstrap.list: Permission denied
Downloading GPG key: [http://linux.dell.com/repo/GPG-KEY-libsmbios](http://linux.dell.com/repo/GPG-KEY-libsmbios)
    Importing key.
gpg: no writable keyring found: eof
gpg: error reading `GPG-KEY': general error
gpg: import from `GPG-KEY' failed: general error
GPG-KEY import failed.
   Either there was a problem downloading the key,
   or you do not have sufficient permissions to import the key.

Can anyone help me with this???

---

### Post by Taus on 2009-07-27
try running this command first:

```
sudo -s
```

i think the bash has to be "sudo"'ed as well

---

### Post by cottfcfan on 2009-07-27
You were right Taus,

I managed to get it to work but no packages could be found to update my Bios.
 Think i`m shafted, unless anyone else has any ideas?

---

### Post by cottfcfan on 2009-07-27
I suppose as a last resort i could re-install my original Dell Vista disk.
 Reset everything to factory settings.
Reinstall my original Bios, and start again with Ubuntu.
 A long drawn out process, but if all else fails.......

---

### Post by cottfcfan on 2009-07-28
So i managed to reinstall the BIOS via windows.
Made no difference.
Still high CPU usage with ACPI on, Normal usage with ACPI=off.
 Has no one else had this problem.
I`m sure there`s someone out there who could help.
Plzzzzzzzzzz

---

### Post by cottfcfan on 2009-07-29
Ive just come across something else.
Since re-installing the bios, i now have a new option in my boot menu, "nvidia boot agent". I ran it and got the message "PXE-E61:Media Test Failure, Check Cable".
Could this be the cause of my problem and the cause of the 20 second hang at "starting up".
Is anyone familiar with this??

---

### Post by cottfcfan on 2009-07-30
These are my latest findings with my problem.
After reinstalling windows Vista begrudginly, to reinstall the BIOS, I did a comparison of CPU usage, this is what I found.

Vista  idling CPU 4-7%
Ubuntu idling CPU 15-20%
Vista  Full Screen Video CPU 20-30%
Ubuntu Full Screen Video CPU 90%+

What is happening here?

By the way I reset the BIOS to factory settings and when I booted back into Ubuntu it worked fine, until I rebooted again.
 Its as if with Linux my BIOS is losing all its settings every time I reboot.

 Is there anyone can help with this?:confused:

---

### Post by twright on 2009-07-30
Ok, then it does look like an acpi/video issue. Try reading through this: [http://www.columbia.edu/~ariel/acpi/acpi_howto.txt]("http://www.columbia.edu/%7Eariel/acpi/acpi_howto.txt")
(edit: you can just skip to the boot parameters)

---

### Post by cottfcfan on 2009-07-30
Thanx for the link twright,
but most of that is way over my head!

---

### Post by cottfcfan on 2009-07-30
OK, Ive found a kind of workaround:

in grub file ive added to the line "kopt=root=/dev/sda1 ro" - acpi=ht apm=power_off.
Then in etc/modules ive added - apm power_off=1.

My system is now quick and responsive, my CPU is down, and I can now play Fullscreen streaming videos perfectly.
The only downside is that ive lost the ability to "suspend"
I just hope that turning off ACPI dosen`t do any damage to my system in any way.:D

---

