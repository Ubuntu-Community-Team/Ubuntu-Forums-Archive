---
title: "Blank Desktop"
date: 2009-12-14
forum: General Help
---

### Post by Igor Stravinsky on 2009-12-14
I powered up my Dell Mini 9 today and there are no desktop icons or menu bars, just a pretty picture and a blank desktop. Computer worked fine yesterday. What do I do? Thanks.

---

### Post by synapsys on 2009-12-14
Perhaps gnome menus have gotten corrupted somehow. Try this:

Press Ctrl+Alt+F1 to drop to a command prompt.

type:
```
sudo dpkg-reconfigure gnome-menus
sudo restart
```

let us know what happens.

---

### Post by Igor Stravinsky on 2009-12-14
Thanks, no luck though. I got a message starting "Can't locate strict.pm in @INC". . .ending in. . .  "BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 8"
 
What now?
Thanks

---

### Post by synapsys on 2009-12-14
You might want to boot up a ubuntu live cd, so you don't have to reboot every time.

try

```
sudo dpkg --configure -a 
```

and see what messages you get.

---

### Post by Igor Stravinsky on 2009-12-14
After I went to the CTRL ALT F1 screen, I had a message that said "usplash: Setting mode 1024x768 failed usplash: Using mode 800x600" Not sure if that is related to my problem, but I figured I'd throw it out there.

---

### Post by Igor Stravinsky on 2009-12-14
I tried 
sudo dpkg --configure -a
No messgages, no change.
Thanks though, any other ideas?

---

### Post by baddog144 on 2009-12-14
> **Igor Stravinsky said:**
> Thanks, no luck though. I got a message starting "Can't locate strict.pm in @INC". . .ending in. . .  "BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 8"
 
What now?
Thanks

That error suggests something is up with your perl installation :/
Did you do anything that might have screwed around with perl at all?

Also, could you please post the output of
```

perl -e 'print @INC;'

```

---

### Post by Igor Stravinsky on 2009-12-14
No, the computer worked fine one day, and not the next....

---

### Post by synapsys on 2009-12-14
```
sudo dpkg-reconfigure perl
```

---

### Post by Igor Stravinsky on 2009-12-14
Thanks,
reconfigure perl gave me the same fail message as last tim (. . . line 8)
 
perl -e 'print @INC;' gave me "/etc/perl/usr/local/lib/perl/5.8.8/usr/local/share/perl/5.8.8/usr/lib/per15/usr/share/per15/usr/lib/perl/5.8/usr/share/perl/5.8/usr/local/lib/site_perl.brian@brian:-$

---

### Post by baddog144 on 2009-12-14
> **Igor Stravinsky said:**
> Thanks,
reconfigure perl gave me the same fail message as last tim (. . . line 8)
 
perl -e 'print @INC;' gave me "/etc/perl/usr/local/lib/perl/5.8.8/usr/local/share/perl/5.8.8/usr/lib/per15/usr/share/per15/usr/lib/perl/5.8/usr/share/perl/5.8/usr/local/lib/site_perl.brian@brian:-$

Hmm, that looks like it's all in order :/ 
I'm at a loss, and I may be barking up the wrong tree anyway :(

---

### Post by Igor Stravinsky on 2009-12-14
Any other ideas?

---

### Post by Igor Stravinsky on 2009-12-14
What if I kick it? Hard.

---

### Post by synapsys on 2009-12-14
Maybe check your filesystem for consistency....

```
fsck /dev/yourubunturootpartition
```

P.S. Don't kick it....yet.....

---

### Post by Igor Stravinsky on 2009-12-14
Is there some keystroke sequence that hides the icons & menus that I may have inadvertantly selected?

---

### Post by synapsys on 2009-12-15
This is an older thread but it sounds like the same problem you're having....

[http://ubuntuforums.org/showthread.php?t=28714](http://ubuntuforums.org/showthread.php?t=28714)

---

