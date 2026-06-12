---
title: "Odd Firefox problem"
date: 2009-08-06
forum: General Help
---

### Post by dark2025 on 2009-08-06
Firefox 3.5 was working fine for me today, but I went to get dinner and now all of a sudden it asked me for a profile, and the profile list was empty. So I pressed cancel and tried it again. This time the profile manager didn't even load up. I mean nothing happens when I click on the icon. No error messages come up when I type 'firefox' into the terminal either. Same results upon restarting. I went to check out my $HOME/.mozilla/ directory to check on my profile, and the entire directory appeared to be empty. I have a slightly older backup available that I tried to copy into .mozilla/ but an error came up saying 'Error moving file: Input/output error'. I did a badblocks check that turned up nothing, and now I'm forced to use gksudo firefox. Does anybody know what could have possibly went wrong in the hour I was away from the computer?

---

### Post by SoftwareExplorer on 2009-08-06
Does it work on a different user?

---

### Post by dark2025 on 2009-08-06
I'm guessing so. I only have the one user, but since gksudo firefox works then it's definitely something specific about my user. My $HOME/.mozilla/ directory being weird like that probably has something to do with it.

---

### Post by dark2025 on 2009-08-06
Anyone?

---

### Post by Hobgoblin on 2009-08-06
I would suggest following [these instructions](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/) to force an fsck then rebooting.

---

### Post by lovinglinux on 2009-08-06
See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by dark2025 on 2009-08-07
Thanks, but it's still the same. I can't do anything to ~/.mozilla, it gives me an input/output error when I try to do something to it, preventing me from deleting it also. Can I just concede that directory and tell Firefox to use a different one for its profiles?

---

### Post by lovinglinux on 2009-08-07
> **dark2025 said:**
> Thanks, but it's still the same. I can't do anything to ~/.mozilla, it gives me an input/output error when I try to do something to it, preventing me from deleting it also. Can I just concede that directory and tell Firefox to use a different one for its profiles?

Try this command to delete mozilla folder:

```
rm -fr ~/.mozilla
```

> **[COLOR="Red"]Note:[/COLOR]** be careful when using **rm -fr**, because if you put the wrong path after it you could delete important folders without warning.

Do you have enough space on the disk? Can you save files on other folders inside your home directory?

---

### Post by dark2025 on 2009-08-07
Thanks, I did that but it's still there. It's odd in that it doesn't give me an error when I delete it, and if I try to delete it in Nautilus it actually disappears, but only to come back again when I do a refresh. I've never encountered an unremovable folder before like this. Yes, I have enough disk space.

It just seems I can't do ANYTHING to ~/.mozilla. Can I make a directory named something like ~/.mozilla.firefox and just make Firefox use that instead? I've already tried creating a symbolic link from .mozilla, but again - input/output error.

---

### Post by lovinglinux on 2009-08-07
> **dark2025 said:**
> Thanks, I did that but it's still there. It's odd in that it doesn't give me an error when I delete it, and if I try to delete it in Nautilus it actually disappears, but only to come back again when I do a refresh. I've never encountered an unremovable folder before like this. Yes, I have enough disk space.

It just seems I can't do ANYTHING to ~/.mozilla. Can I make a directory named something like ~/.mozilla.firefox and just make Firefox use that instead? I've already tried creating a symbolic link from .mozilla, but again - input/output error.

Go to "System >> Administration >> System Monitor" and kill everything with firefox in the name. It seems Firefox it's not closed, that's why it creates ~/.mozilla after you refresh Nautilus. You can't delete ~/.mozilla while Firefox is running.

---

### Post by dark2025 on 2009-08-07
It's still not working. I don't think that it's being recreated, I think there's something wrong with the folder itself (hence appearing empty, can't be modified, returning input/output errors, etc). It looks like it might be beyond rescue.

---

### Post by lovinglinux on 2009-08-07
> **dark2025 said:**
> It's still not working. I don't think that it's being recreated, I think there's something wrong with the folder itself (hence appearing empty, can't be modified, returning input/output errors, etc). It looks like it might be beyond rescue.

Those input/output errors happens when you try to delete a profile with Firefox running. Are you sure Firefox is not running?

---

### Post by dark2025 on 2009-08-07
I first encountered that error when I was* adding* files into ~/.mozilla (trying to get my backup profile in there), and yes, Firefox was completely closed. I've done a few restarts too to no effect.

---

### Post by lovinglinux on 2009-08-07
> **dark2025 said:**
> I first encountered that error when I was* adding* files into ~/.mozilla (trying to get my backup profile in there), and yes, Firefox was completely closed. I've done a few restarts too to no effect.

Try this:

```
firefox -P
```

If the Profile Manager shows up, create a new profile and start it.

---

### Post by dark2025 on 2009-08-07
Thanks, but that didn't work either. The profile manager never shows up. It appears if I run it as root with gksudo, but then I can only manage the profiles associated with the root account. Right now I can only use Firefox as the root user.

---

### Post by aysiu on 2009-08-07
Have you tried rebooting?

---

### Post by dark2025 on 2009-08-07
Yes, I have, to no effect.

---

### Post by aysiu on 2009-08-07
Well, that i/o error is concerning. It could be reflective of some hardware issue.

Have you tried running fsck on it with a live CD?

---

