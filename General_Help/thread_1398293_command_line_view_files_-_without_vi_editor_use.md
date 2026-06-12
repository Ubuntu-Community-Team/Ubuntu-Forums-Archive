---
title: "command line view files - without vi editor use"
date: 2010-02-04
forum: General Help
---

### Post by jenaniston on 2010-02-04
While I have usually just used vi editor as . . . # vi *filename.ext* to view a file contents . . .
and then certainly force a quit without write by** :q!** . . .

as I am now in recovery root terminal getting into some files like /boot/grub/menu.lst and etc/fstab that 
I* just* want to view and review *only* first,
I would rather just view them while in this recovery root terminal mode -
and after I learn exactly what change to tweak in -
then and only then *actually* use the vi or other editor as needed.

So, is there a way to** just view file contents** . . . 
when there is no need or desire to edit and thus avoid any chance of a mistake
 or swap file left for some very critical boot up files that I don't really understand yet anyway.

Thank you very much.

---

### Post by darius.k on 2010-02-04
Use **cat** or **more** to view file contents.

---

### Post by doas777 on 2010-02-04
cat <filepath>

---

### Post by DaithiF on 2010-02-04
if you are familiar with and like the navigation style of vi/vim then you could use view, which is vi in readonly mode, so
```
view somefile
```
which is equivalent to
```
vi -R somefile
```

---

### Post by jenaniston on 2010-02-04
> **darius.k said:**
> Use **cat** or **more** to view file contents.

> **doas777 said:**
> cat <filepath>

Duh . . . ok,
I actually was stuck with vi editor in a file that was entirely empty file -
/proc/acpi/event
and I couldn't even get out with the **:q!**

And that empty file - 
which I left empty and without any swap file by *unplugging* power and rebooting -
when viewed with both** cat** and **more** . . .
 I needed to **ctrl-C** to get back to the command prompt from the empty screen.

[http://linux.die.net/man/1/cat](http://linux.die.net/man/1/cat)

[http://linux.die.net/man/1/more](http://linux.die.net/man/1/more)

Thanks again . . . I'll try to answer other newbie questions - where I can -
 to help out all of your your work in support of Debian and linux.

---

### Post by doas777 on 2010-02-04
if you need to ctrl+c out of cat, then somthing is wrong. am I misunderstanding your statement?
it may be that the file is very large, and is taking a long time to load, or it may be that while the file appears empty, it is actually full of many blank lines. usually cat will output like this```

karmic:~$ cat .dmrc


[Desktop]
Session=default
Language=en_US.UTF-8
Layout=us
karmic:~$ 

``` returning control to the prompt, as soon as the file is done printing. is this not happening for you?

I've had some issues with exiting vi over the last year as well, but usually after trying the same thing a few times, one of them sticks.

ps: I always use nano over vi. perhaps it is a good option for your needs. exit it with Ctrl+X, and say no if you don't want to save.

---

### Post by jenaniston on 2010-02-04
> **DaithiF said:**
> if you are familiar with and like the navigation style of vi/vim then you could use view, which is vi in readonly mode, so
```
view somefile
```which is equivalent to
```
vi -R somefile
```

Thanks . . . hah, I just tried ```
view /proc/acpi/event

```and again as with vi editor (which I guess it really*** is*** anyway)  -
 it left me *without* a way out for this totally empty file -
maybe because I'm in a recovery mode root terminal screen ?

Either . . .

**<Esc>** (I never went to insert mode anyway)
**<Ctrl-C>**
**:q!**

. . . all still left me with the blank . . . empty file . . . screen.

So I'll unplug power again - for last time - as the only way out . . .

Thanks everybuddy for the advice with quick replies.

---

### Post by hemimaniac on 2010-02-04
to view a file without modding it, I use nano

$ nano /name/of/some/file

all the commands you would need are listed at the bottom (basic) and if you do actually accidentally change something (though without the <sudo> cmd issued first for a file outside of your home directory you wouldn't be able to save changes anyway.

to close out you would simply do ^x and answer no

now there alot of ways to do what you would like to do, nano is just a personal preference for myself

---

### Post by jenaniston on 2010-02-04
> **doas777 said:**
> if you need to ctrl+c out of cat, then somthing is wrong. am I misunderstanding your statement?
it may be that the file is very large, and is taking a long time to load, or it may be that while the file appears empty, it is actually full of many blank lines. usually cat will output like this

I've had some issues with exiting vi over the last year as well, but usually after trying the same thing a few times, one of them sticks.

ps: I always use nano over vi. perhaps it is a good option for your needs. exit it with Ctrl+X, and say no if you don't want to save.

I have been having some unusual workings with this vi editor . . .
remindful that I am in the recovery kernel (2nd choice on boot up) - so that could be a factor ?

The file is definitely empty . . .
all blue ~ "lines" and I also tried cat -n to number any lines - nothing still.

Also, I have had the empty screen on very long on the laptop - as I have been posting here while on another computer from a campus library on the same desk.

This is *some sort* of acpi event file that logs events . . .
and now guess what . . .

I just tried the power button to turn off instead of unplugging the cord
and it*** did ***log that as an event -
so** NOW** I do have actually one line in the file . . .
```
button/power PWRF 00000080 00000001
~
~
~
~
~
...
```but it did not turn off power - just logged an entry that I pressed the button -
and now I could **:q!** out back to prompt and never did turn power off.

I ***am*** in as root - and recovery mode gives full write permissions.
This file is *weird* . . .:roll:

Go figure . . .

Thanks again for the interest - and I'll look into nano editor more too.

---

### Post by Bachstelze on 2010-02-04
How about you tell us what you want to do, exactly?

---

### Post by jenaniston on 2010-02-04
> **Bachstelze said:**
> How about you tell us what you want to do, exactly?
Our apologies to all the international members of the forum as translations can be tricky . . .
but these simple commands are a sufficient solution.
> **darius.k said:**
> Use **cat** or **more** to view file contents.
  
 > **doas777 said:**
> cat <filepath>
 
and I included the link to the full manual page to help any other newbies.
> **jenaniston said:**
> . . .
when viewed with both** cat** and **more** . . .
 I needed to **ctrl-C** to get back to the command prompt from the empty screen.

[http://linux.die.net/man/1/cat](http://linux.die.net/man/1/cat)

[http://linux.die.net/man/1/more](http://linux.die.net/man/1/more)

Thanks again . . . I'll try to answer other newbie questions - where I can -
 to help out all of your your work in support of Debian and linux.

So the only other question is why this may happen . . .
and why **ctrl-C** was needed to even exit from a **cat** or **more** command
Is this only a vi editor phenomena or with only this kind of file . . . I dunno.

I ***never did*** want to edit this /proc/acpi/event file . . . just view it safely . . .
and it probably can NOT even be edited . . . even by a root user. :roll:

---

### Post by Tibuda on 2010-02-04
when i just want to view files, I just use less.

---

### Post by jenaniston on 2010-02-04
> **danielrmt said:**
> when i just want to view files, I just use less.

Well, with this *originally* empty file . . . **less** did *about* the same as the opposite command **more**.

With both **more** and** less** commands the empty file after hitting the power button (although laptop would stay on)
added a line as stated earlier to record the event.

**ctrl-c** with **more** command then returned to prompt
**ctrl-c** with** less** command gave a colon escape character like vi usually does and after I added q it quit back to the prompt . . .
but again only if their was something actually in the file . . . like the one line added
after I hit the power button to **record an acpi event** and add an entry.

So, thanks **danielrmt** . . . a nice little trick also.

[http://linux.die.net/man/1/less](http://linux.die.net/man/1/less)

---

### Post by doas777 on 2010-02-04
the only thing I can think of, is that file is locked by another process, and cat/vi/nano/etc are waiting stuck in a deadlock, until the locking process releases (which may not be happening until reboot). that is unusual since most locks are only for write, not for read, so cat should be able to complete without deadlocking.

 not sure what to tell you

---

### Post by Bachstelze on 2010-02-04
> **jenaniston said:**
> 
So the only other question is why this may happen . . .
and why **ctrl-C** was needed to even exit from a **cat** or **more** command
Is this only a vi editor phenomena or with only this kind of file . . . I dunno.

I ***never did*** want to edit this /proc/acpi/event file . . . just view it safely . . .
and it probably can NOT even be edited . . . even by a root user. :roll:

What happens is that the files in /proc are virtual, which means their content is not stored anywhere, and is dynamically generated by the kernel when you want to access them. This meas that 1) you obviously can't edit them, and 2) opening them in an editor like [font=monospace]vi[/font] might lead to the strange behaviour you're seeing. The correct way to view these files is by using [font=monospace]cat[/font]:

```
cat /proc/acpi/event
```

If the file is big and you want to browse through it, pipe the output to [font=monospace]less[/font]:

```
cat /proc/acpi/event | less
```

If you want to make a copy of the file for further reference, you can use shell redirections to dump the output to a file instead of standard output:

```
cat /proc/acpi/event > event.txt
```

---

### Post by jenaniston on 2010-02-04
> **Bachstelze said:**
> What happens is that the files in /proc are virtual, which means their content is not stored anywhere . . .
. . . If you want to make a copy of the file for further reference, 
you can use shell redirections to dump the output to a file instead of standard output:

```
cat /proc/acpi/event > event.txt
```

All great to know . . . for me and other newbies.

Merci beaucoup.

---

