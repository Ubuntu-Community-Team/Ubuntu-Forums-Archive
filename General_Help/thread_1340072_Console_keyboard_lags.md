---
title: "Console keyboard lags"
date: 2009-11-28
forum: General Help
---

### Post by Unchqua on 2009-11-28
Hello guys!

   I have a small discomfort with my 9.10 installation, which otherwise works well thanks to all the work Ubuntu contributors made for all of us. Problem is a terminal console, which lags outputting symbols I type. Test is simple: open default ternimal (gnome-terminal by default) and hold down any letter key. Symbols start appearing until 1-2 seconds pass, then further letters stop show itself for about 1 second, then they all displays on screen at once (keyboard buffer plays here?) and continue grow for another 1-2 seconds interval; then everything described repeats again.
   In any GUI application there's no such behaviour, keyboard input and screen output are quick and precise. First I thought it's a fault of gnome-terminal, but in plain old xterm it's the same problem.
Can anybody give me an advice on what to do with this? How can I tell for sure which system component is responsible?

---

### Post by Xbehave on 2009-11-28
I have similar issues, but only when compiz is running, does it work ok when desktop effects are turned off?

---

### Post by Unchqua on 2009-11-28
I had latest  NVidia driver from official Ubuntu feeds plus standard effects turned on (never saw a reason so that, just tried it out of curiosity). Now NVidia proprietary driver has been uninstalled, effects turned off, but console still lags. What I know now is that it's not a keyboard side of problem, because console application, rtorrent BitTorrent client, also "delays" its screen drawings: it outputs its information quicker than once per second, but visible screen update is obviously delayed.

---

### Post by Xbehave on 2009-11-29
Keep nvidia drivers, but leave effects off, does it still happen then?
And does it happen when you use command line logins? (press ctrl+alt+f2, then ctrl+alt+f7 OR ctrl+alt+f1 to get back to the graphical login)

---

### Post by Unchqua on 2009-11-29
Thanks for still helping me **Xbehave**!
No, proprietary driver installed doesn't help regardless if effects are on or off. Text mode suggested by you (ctrl-alt-f2 and back) shows the same lags, which is really strange.
I thought that it's /dev/tty who delays output for some reason, and tried this to find it out:
```
while true; do echo -n t >/dev/tty; sleep .1; done
```Output is a string tttttttttttttt growing every 1/10 second. And that's strange. Yesterday when I launched this command for the first time, output was jerky, and I thought that was it, the problem is in tty. But relaunching this several times after there were no lags. Now I'm trying it again, and jerks are here no matter how much I issue this while loop. But this experiment might not be clean since I freshly open /dev/tty on every loop.
```
strace -o ttytest -tt /bin/dash
```doesn't reveal anything useful regarding times.

---

### Post by Xbehave on 2009-11-29
np, just wish i could actually be useful. 

If you used the text mode (ctr+alt+f2 & login) and it was still slow then this is over my head

The tests you did are over my head tbh, but it sounds like its a bug with all ttys, perhaps you could test a different kernel 
The easiest way to do that is to get an older/newer liveCD, but if our feeling more adventurous I think ubuntu offers a "mainline" kernel which is probably a different versions to yours but is unsupported.

---

### Post by Unchqua on 2009-11-29
Thanks **Xbehave**, I'll boot several LiveCDs I can reach to, starting with original 9.10 which I used to install Karmic, to see if it's OK there with console output. Thanks again.

---

### Post by jj9 on 2009-12-07
Confirmed the same problem on my netbook, an Acer Aspire 1410 running Karmic and 2.6.31-16.  In all types of terminals, and even in the text console (Ctrl+Alt+F1, etc.), I get a periodic "freeze" for roughly half a second to maybe two or three seconds while typing.  It's quite irritating!  It's not unlike being over a connection.

As noted, the fact that it happens even in the console makes it particularly perplexing, and yet it is absent in other applications, such as the textbox I'm typing into right now.  Or at any rate what pauses there are are much shorter and less frequent.

I'd be interested if any solution or insight exists.  I've been toying with all manner of various settings to no avail.

---

### Post by jj9 on 2009-12-07
Ok I believe I've figured out what caused this issue in my case.

I was running an application which repeatedly queries /proc/acpi/battery to track the battery level.  Apparently just reading this file causes a freeze-up of several parts of the system, including console typing.  Why, I'm not really sure, but removing this feature caused a number of things to behave more smoothly, including a clock application.

As I understand, this acpi stuff is mostly deprecated, although I'm not sure what's meant to be used in its place.  At any rate anyone with this problem might want to start thereabouts.  Best of luck.

---

### Post by Unchqua on 2009-12-08
Strangely enough I see no freezes on my EeePC running the same Karmic. What ACPI application are you talking about, is it "standard" (came with default Ubuntu installation)? If so I'll try to disable it and see if this helps. Curious how did you find the cause.

---

### Post by jj9 on 2009-12-09
No it was not a standard application, but something I wrote myself.  It read the battery state from /proc/acpi/battery/BAT1/state repeatedly.  Trying to do that manually takes oddly long, like a second or two.  Removing the application that made this query repeatedly caused the pausing/stalling/lagging effect to more or less go away.  There does still seem to be a minor sporadic lag, but it's tiny compared to before.

That's all I know.  I don't know what could be causing this on your end.

---

