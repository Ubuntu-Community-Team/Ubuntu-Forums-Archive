---
title: "&quot;Google chrome didn't shut down correctly.&quot; message after restart."
date: 2010-04-13
forum: General Help
---

### Post by ubername on 2010-04-13
Hi

When I restart / shutdown without closing Chrome, the next time I open it I get the "Google chrome didn't shut down correctly." message. I guess this is to be expected but can anyone suggest a way to close chrome elegantly on shutdown / reboot?

---

### Post by sh4d0w808 on 2010-04-13
It is very elegant to close Chromium via the X button... or write a kill script which runs on shutdown.

---

### Post by ubername on 2010-04-13
> **sh4d0w808 said:**
> It is very elegant to close Chromium via the X button... or write a kill script which runs on shutdown.

Very droll...

The kill script on shutdown sounds like what I am after -  how would I do that?

---

### Post by scouser73 on 2010-04-13
Just clicking x should shut down Chrome without you seeing a message next time it's used.

---

### Post by cong06 on 2010-04-13
> **ubername said:**
> Very droll...

The kill script on shutdown sounds like what I am after -  how would I do that?

I don't know, I'd have to agree with his Idea, the "x" is very effective.

That being said, there's always man pages dealing with the kill command:
```

man kill

```

I'm worried though that using kill will give you the same effect ask shutting down, since shutting down really just calls the kill command.

---

### Post by sh4d0w808 on 2010-04-13
I do not know, why the X is not enough good, but then write a script which query only chromium-browser processes, awk it to get only the process ID, then put it to the suitable rc directory and runs it before the GUI shuts down... I think it will be so hard...

---

### Post by yochel on 2010-04-13
If your cumputer siezes up, there is not really anything you can do about it, but usualy, you can restore the previous tabs. Otherwise, simply clicking the 'X' botton (or indevidualy closing all the tabs) should work fine.

---

### Post by ubername on 2010-04-15
Sorry, I seem to have created the wrong impression here. I can perfectly well shut chrome with the 'x' button, and my computer is not freezing up.

My point is that I want to be able to simply restart the computer without doing that (or closing any other apps), and still have chrome behave as if I had closed it 'cleanly'. I have set my preferences to remember what I had open when I last logged in and it seems to work fine, except that chrome has this 'feature'.

---

### Post by cong06 on 2010-04-15
> **ubername said:**
> I have set my preferences to remember what I had open when I last logged in and it seems to work fine, except that chrome has this 'feature'.

Short of screwing around with chrome I'm not sure what you'd do.

I'm sure you know all about kill... It won't close the program the way it was "intended" since chrome probably has some mechanism to detecting if the program was closed the way it wanted.

I wonder how hard it would be to disable this feature.
It's interesting because Firefox doesn't complain at all about being closed by an outside program.... well, sometimes it gives me "this is embarrassing" and then goes to restore all my tabs (even though it failed??)

---

### Post by ubername on 2010-04-15
Interesting - Chrome now doesn't start automatically when I login again (I wonder if I am imagining that it ever did?) Whatever - even if I set the preferences in chrome to 'open the following pages' on startup, I still get the message about not shutting down cleanly (which does kind of make sense) when I manually restart it.

---

### Post by joshruehlig on 2010-05-05
This has been annoying me too. Its pretty nit-picky but I don't want to have chrome always ask me to restore tabs after a shutdown.

I want to be able to turn off my netbook, with chrome open and when I turn it back on for chrome to already have the tabs open, not always ask.

I wrote a script to close chrome properly when I shutdown/reboot.
-------------------------
cat /etc/init.d/killchrome.sh
#!/bin/sh
killall -I chrome
-------------------------

If I run this it closes chrome, if I reboot, when chrome opens the tabs are properly restored. Made it executable. I made a link to this file in /etc/rc0.d and /etc/rc6.d naming the files K01killchrome.sh
**But a reboot or shutdown doesn't work. Chrome is still prematurely closed.** After a reboot it asks to restore tabs... I also tried K99killchrome.sh

Anyone who knows about running scripts very early in the shutdown&reboot process please guide us in the right way. Thanks
I ran

---

### Post by ubername on 2010-05-09
FWIW, Firefox behaves exactly as I would like chrome to - I can simply reboot with firefox open and when I log back in again, Firefox reopens exactly as I had left it.

---

### Post by cong06 on 2010-05-10
> **joshruehlig said:**
> 
Anyone who knows about running scripts very early in the shutdown&reboot process please guide us in the right way. Thanks
I ran

It seems like this is all...

And I have to admit, I'm rather interested in this also now. (even though I insulted the OP early on... sorry dude)

---

### Post by renkinjutsu on 2010-05-10
> **cong06 said:**
> Short of screwing around with chrome I'm not sure what you'd do.

I'm sure you know all about kill... It won't close the program the way it was "intended" since chrome probably has some mechanism to detecting if the program was closed the way it wanted.

I wonder how hard it would be to disable this feature.
It's interesting because Firefox doesn't complain at all about being closed by an outside program.... well, sometimes it gives me "this is embarrassing" and then goes to restore all my tabs (even though it failed??)

Kill has several different layers to it. there's the SIGTERM which signals the program to terminate as opposed to just terminating the program.

I just tried invoking kill like this: ```
kill -TERM $(pgrep chrom)
```
and it's working to shutdown chromium. When i open up chromium again, it doesn't ask me to restore anything

---

### Post by joshruehlig on 2010-05-11
renkinjutsu

kill -TERM $(pgrep chrom) 

works just like the command I gave for chrome **but does not work when putting in /etc/init.d/ and assigned runlevel 0 and 6**

This would be cool to figure out, saves me a click when turning on the computer.

Something is killing chrome before my command can be run...

---

### Post by renkinjutsu on 2010-05-13
chrome is being killed before you command runs because the first thing that happens when you shutdown your computer is X terminates.. and when X terminates, all graphical applications go with it.

You can alias your shutdown command to do something like:
```
alias shuthalt='kill -TERM $(pgrep chrome); poweroff'
```
or create an executable file that does that and use that file instead of the regular "shutdown" or "poweroff"

---

### Post by joshruehlig on 2010-05-13
I still want to be able to turn of my computer with the power button, how I do it now so running a script wouldn't work. Thanks! So is that command persistent or do I need to run it every boot?

alias shuthalt='kill -TERM $(pgrep chrome); poweroff'

---

### Post by cong06 on 2010-05-15
What would be interesting is to find out where this script is. Learn where the X server is killed, and insert the previously mentioned chrome kill command.

---

### Post by fragos on 2010-05-15
I would concur that the shutdown operation of Chrome is a little different than say Firefox. I don't find the difference objectionable but if you do file a bug. I just updated to "6.0.401.1 dev" but haven't yet rebooted with this new version.

---

### Post by joshruehlig on 2010-05-17
Yeah I wonder what is run when going into the shutdown and reboot runlevels. obviously something is run before stuff in the /etc/rc0.d folder.

---

### Post by ubername on 2010-05-17
> **cong06 said:**
> It seems like this is all...

And I have to admit, I'm rather interested in this also now. (even though I insulted the OP early on... sorry dude)

You're forgiven - I didn't actually realise it was an insult - just good natured banter, I thought!

---

### Post by joshruehlig on 2010-05-17
I wish I used firefox really, the bar in chrome is just better then firefox, even then firefoxs omnibar. Chromes predicts what i want better and i dont need to click nearly as much

ex. to click go to youtube through the bar i type y - enter
firefox is y-down-enter

and searching with y-tab-search is way faster then firefox could do...

but I wish i could use firefox for better syncing, passwords/fennec browser

---

### Post by Dysport on 2010-06-25
Although this isn't really an elegant solution and may even cause errors on some systems, here is what I just did:

1.) Moved the original shutdown and reboot script to new locations:
~$ sudo mv /sbin/reboot /sbin/reboot_original
~$ sudo mv /sbin/shutdown /sbin/shutdown_original

2.) Created new bash scripts that invoke the "…_original" ones but kill chrome first:
~$ sudo nano /etc/shutdown
```
#!/bin/sh
kill -TERM $(pgrep chrom)
args=`getopt r:h:H:P:ckqv $*`
/sbin/shutdown_original $args
```
~$ sudo chmod +x /etc/shutdown

~$ sudo nano /etc/reboot
```
#!/bin/sh
kill -TERM $(pgrep chrom)
/sbin/reboot_original

```
$ sudo chmod +x /etc/reboot

As I said, works fine for me, could screw up things even worse for you. No guarantees here.

---

### Post by joshruehlig on 2010-06-25
> **Dysport said:**
> Although this isn't really an elegant solution and may even cause errors on some systems, here is what I just did:

1.) Moved the original shutdown and reboot script to new locations:
~$ sudo mv /sbin/reboot /sbin/reboot_original
~$ sudo mv /sbin/shutdown /sbin/shutdown_original

2.) Created new bash scripts that invoke the "&#8230;_original" ones but kill chrome first:
~$ sudo nano /etc/shutdown
```
#!/bin/sh
kill -TERM $(pgrep chrom)
args=`getopt r:h:H:P:ckqv $*`
/sbin/shutdown_original $args
```
~$ sudo chmod +x /etc/shutdown

~$ sudo nano /etc/reboot
```
#!/bin/sh
kill -TERM $(pgrep chrom)
/sbin/reboot_original

```
$ sudo chmod +x /etc/reboot

As I said, works fine for me, could screw up things even worse for you. No guarantees here.

I was sure this would work. The commands killed chromium just fine but when everything was setup neither shutdown or reboot kill chrome in time... I could implement a sleep in there but that would slow down reboot times... maybe worth it actually

Im on a fairly fast SSD on a netbook so processes might run in weird orders because the ssd seeks fster then the processor can do some commands... so the future commands might finish before the killchrome was fully done

---

### Post by Dysport on 2010-06-25
> **joshruehlig said:**
> I was sure this would work. The commands killed chromium just fine but when everything was setup neither shutdown or reboot kill chrome in time... I could implement a sleep in there but that would slow down reboot times... maybe worth it actually

Im on a fairly fast SSD on a netbook so processes might run in weird orders because the ssd seeks fster then the processor can do some commands... so the future commands might finish before the killchrome was fully done

Have you experimented a bit how long the sleep would have to be? I'm sure you can afford to lose 1 or 2 seconds.

Another solution I've thought of would be to write a little daemon that runs on xserver session startup and just before it gets killed it nicely closes Chrome. I don't have the time to write one right now but I might get round to do it next week.

---

### Post by fragos on 2010-06-25
In my experience if you manually close Chrome before shutdown it may have more time to terminate completely. Chrome starts a number of separate processes and the all need to terminate. To me this was such a small issue that I didn't file a bug report. Perhaps you should.

---

### Post by joshruehlig on 2010-06-26
I definitely can, shutdown time doesn't matter at all to me, (as long as its under 5sec). I'll experiment with it a little bit later this weekend.

---

### Post by Dysport on 2010-06-26
> **fragos said:**
>  I didn't file a bug report. Perhaps you should.

I don't think it's appropriate to file a bug report here because in most situations this is a very useful feature, the ability to restore your crashed session with just one click. On my other computes this YBOD (yellow bar of death) has already saved me quite some time, imagine restoring multiple windows with 10-20 open tabs each.
And for the sake of speed Ubuntu doesn't end all possible processes 'nicely' which I perfectly understand. OS X does that and it can take ages just to shut down.

---

### Post by Dysport on 2010-06-26
I just tried to use a Python script instead of bash. Closing chrome works nicely but the computer will hang later in the shutdown process (probably when /sbin/shutdown is invoked again but python's not available anymore).

EDIT: Let me know whether this works for you:
/sbin/shutdown:
```
#!/bin/sh
t=`/sbin/pidof chromium-browser`

while [ -n "$t" ] # while chrome is running 
do
`/bin/kill -TERM $(pgrep chrom)`
t=`/sbin/pidof chromium-browser`
done

if [ -z "$t" ] # if it's not running:
then
args=`getopt h:r:H:P:ckqv $*`
/sbin/shutdown_original $args
fi
exit 0

```

---

### Post by fragos on 2010-06-26
> **Dysport said:**
> I don't think it's appropriate to file a bug report here because in most situations this is a very useful feature, the ability to restore your crashed session with just one click. On my other computes this YBOD (yellow bar of death) has already saved me quite some time, imagine restoring multiple windows with 10-20 open tabs each.
And for the sake of speed Ubuntu doesn't end all possible processes 'nicely' which I perfectly understand. OS X does that and it can take ages just to shut down.

The bug would relate to the message appearing when Chrome was closed by user action like a Shutdown or Exit.

---

### Post by Dysport on 2010-06-26
> **fragos said:**
> The bug would relate to the message appearing when Chrome was closed by user action like a Shutdown or Exit.

… as stated before, wouldn't that be 'Ubuntu's fault' for not ending processes nicely on a user triggered shutdown or reboot? The way I see it the Chrome processes are just terminated by Ubuntu rather than 'cleanly killed' - which is why Chrome can't distinguish whether it's crashed or been shut down.
But please, correct me if I'm wrong.

---

### Post by eltonw on 2010-06-26
IMVHO, everyone seems to be missing the main point: **Google Chrome** is a **BETA**_ ... as such, bugs *are to be expected*_. I myself find that no matter how I shut down this browser, the same error message frequently occurs. It's neither the fault of the user nor the OS. _More likely it is a BUG in the program itself_.

The best thing would be to report this to the developers, or await an update. FWIW, I simply consider this as a minor annoyance. There are far more serious issues regarding the OS itself and / or other applications.

respectfully,

---

### Post by fragos on 2010-06-26
> **Dysport said:**
> … as stated before, wouldn't that be 'Ubuntu's fault' for not ending processes nicely on a user triggered shutdown or reboot? The way I see it the Chrome processes are just terminated by Ubuntu rather than 'cleanly killed' - which is why Chrome can't distinguish whether it's crashed or been shut down.
But please, correct me if I'm wrong.

Regardless of where the problem lies it's still a bug with a cause we can guess at but not identify. The bug may lie in how the kernel closes applications or in how Chrome interprets system information about how the multiple processes were closed or how one of the processes recorded it's closure or a combination of all. There's nothing wrong with reporting a bug to the application where it is consistently seen. The bug process handled by the engineers has the ability to to reassign the bug. As an engineer my first question would be why does Chrome display that message and work from there.

---

### Post by Dysport on 2010-06-26
I see. Thanks eltonw and fragos for your inputs!

---

### Post by tulskiy on 2010-07-28
Do they really just send kill to every process? If I'm trying to restart with VirtualBox machine running, the machine shows dialog like 'Power off the Machine?, etc', and Ubuntu says that the program is still running and killing it may damage data.

So, either applications may detect that they are being killed and stop this process or take some actions before it, or Ubuntu makes the decision about killing a process by itself?

---

### Post by christophermluna on 2010-08-16
Okay, I've also had this problem for some time.  And for the longest time, I simply tolerated it.  But recently, having gotten most of the bells and whistles working on my new computer, having ironed out most of the issues with my install (odd hardware), I have started to look into this.

For me it happens often even when I close Chrome with the 'X,' which was what was most infuriating.  And this link is the closest thing I could get to figuring out why:

[http://groups.google.com/a/chromium.org/group/chromium-discuss/browse_thread/thread/582f428deed37d4a]("Sync and Google Chrome")

This guy seems to think it has to do with Google's Syncing.  His explanation makes sense from where I'm sitting, because I'm connecting through some kind of terrible excuse for broadband in China.  Aiya.

Anyway, the syncing thing might work.  I will give it a go.

But the work around proposed in the above site is not ideal by any stretch of the imagination, and I think the issue is one that the Google folks will have to iron out.

~Luna

---

### Post by Dysport on 2010-08-17
I've never had sync turned on at all.

---

### Post by christophermluna on 2010-08-17
Sorry to hear that.  So far, turning sync off has worked for me, but we'll see.

---

