---
title: "thinkpad laptop suspend not working properly after upgrading Breezy to Dapper"
date: 2006-06-04
forum: General Help
---

### Post by d3wu on 2006-06-04
Suspend for Breezy was working perfectly on my T41p thinkpad.  Then I updated to Dapper and now Fn-F4 (suspend button) doesn't work for me.  :-k 

I noticed in /etc/acpi/sleep.sh, the script will exit if klaptopdaemon is running.  After removing klaptopdaemon and manually executing /etc/acpi/sleep.sh, it suspends but exits out of x windows.  Fn-F4 still doesn't call /etc/acpi/sleep.sh i believe, since I could get it to actually suspend by typing it into the console but not by pressing Fn-F4.

On resume I still get the console and have to hit CTRL-ALT-F7 to return to x windows.

I'd like to get suspend working in Dapper like it was for Breezy - FN-F4 would suspend it in X Windows.  On resume, it would return to X Windows automatically.  Any info would help! Thanks

---

### Post by matt_man22 on 2006-06-04
I'm running Dapper on a T42 and it suspends fine.  Usually Ubuntu works well with Thinkpads.  Maybe a fresh install might help.  Also, sometimes using the fglrx driver breaks suspend mode.

---

### Post by d3wu on 2006-06-04
yeah i figured it was the breezy to dapper upgrade that broke things. 

maybe the fglrx version i was using in breezy worked with suspend, and the new dapper driver ( 8.25.18 ) broke it?

any insights?

---

### Post by slimdog360 on 2006-06-04
I dont know if this will help, but it made ine work (im using an ibm thinkpad R50e).
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R50e#Standby.2C_Sleep_and_Hibernation]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R50e#Standby.2C_Sleep_and_Hibernation")

---

### Post by d3wu on 2006-06-10
hm..i tried the wiki - no luck though..

im thinking about reinstalling the suspend-related programs  (acpi, etc).  which other programs should i reinstall for this?

---

### Post by OctaneZ on 2006-06-16
I too am having trouble with suspend and hibernate on a T42 (2373-3VU).
I have uncommented "ACPI_SLEEP" and "ACPI_HIBERNATE" in /etc/defaults/acpi-support.
Anyone had luck yet?

---

### Post by splitsch on 2006-06-17
Hello !
Check this post:
[http://www.ubuntuforums.org/showthread.php?t=187584&highlight=r50e](http://www.ubuntuforums.org/showthread.php?t=187584&highlight=r50e)
I solved it for my thinkpad r50e !
you also must enable sleep  in the acpi-support file !

---

### Post by joe_geek on 2006-06-17
[QUOTE=OctaneZ]I too am having trouble with suspend and hibernate on a T42 (2373-3VU).
I have uncommented "ACPI_SLEEP" and "ACPI_HIBERNATE" in /etc/defaults/acpi-support.
Anyone had luck yet?[/QUOTE]

Same thing for me, T40.  Suspend and hibernate just hang.  Screen goes blank but it doesn't complete either process fully.

---

### Post by axelb on 2007-02-11
Perhaps a bit late to join, but, yes: I have the same problem. I have upgraded from breezy to dapper, and here is my experiences:

First: There are (at least) two bug reports for this:
[INDENT]    [https://launchpad.net/ubuntu/+bug/47508](https://launchpad.net/ubuntu/+bug/47508) (suspend and hibernate)
    [https://launchpad.net/ubuntu/+source/acpi-support/+bug/40621](https://launchpad.net/ubuntu/+source/acpi-support/+bug/40621) (suspend and vbetool)[/INDENT]
[COLOR="Blue"][SIZE="4"]
**Remove totally and reinstall**[/SIZE][/COLOR]
After having experimentet around with tips on some of the links mentioned here, I decided to remove almost everything connected to hibernation and sleep functions, because, clearly, it was the upgrade that broke it.
I ran: 

[INDENT]    *sudo apt-get remove --purge powersaved, kpowersave, acpi*, klaptopdeamon kde-guidance*[/INDENT]

As expected, suspend to RAM (Fn+F4) and to disk (Fn+F12) does not work anymore (no reaction).
I then installed just the acpi part:

[INDENT]    *sudo apt-get install acpid acpitools acpi-support kde-guidance*[/INDENT]

and found, that the scripts installed by  acpi-support in /etc/acpi actually worked, but the Fn+F4 and Fn+F12 still don't give anything.
To be exact: **hibernation.sh** worked as is, but **sleep.sh** had to be altered and **xorg.conf**, as [ described here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R50e")
I also changed /etc/default/acpi-support as described.

**tpb** or **kmilo** (both will work) actually got most of the other keys to work (but not the Access IBM button--se the mentioned thinkwiki.org pages there are many, linked together in one complex).

[SIZE="4"][COLOR="Blue"]**Klaptopdaemon**[/COLOR][/SIZE]
I then reinstalled the klaptopdaemon, and the keys still does not work, but I can monitor my battery power.
And from the Klaptop menu (a battery icon in the panel) I can choose Suspend to disk and suspend to RAM. This is what happens:

**Suspend to RAM:** It locks the screen and I am not able to log in again, no matter what password I give it tells me it is wrong. I have tried resetting the password to just "q", but it still don't work. (*See below for more on this particular bug*). Alt+Ctrl+Delete works, though, so I can log in again. Better than starting all over.
**Suspend to disk**: Same as above.

[COLOR="Blue"][SIZE="4"]**Kpowersave**[/SIZE][/COLOR]
Then I tried just powersaved, but it gives the described weird behavior, so I think this package is broken concerning these machines (all or most IBM Thinkpads probably). This is what happens:

**Suspend to disk**: Logges me out, when I am back, it is as if I had just restarted the machine. It seems it gives me GUI and then throws me out again because the process is similar to the one being performed by hibernation.sh (see above), except this time it don't work
**Suspend to RAM**: Freezes totally, I can't even use Alt+Ctrl+Escape to restart, I have to use the power button.

**Kpowersaved** gives the exact same result (as expected since it uses powersaved as its basis).
It has not the same scripts as acpi, it has it's own.

I still have not tried the **manual method of defining keycodes** etc. But the thinkwiki-pages ([http://www.thinkwiki.org/wiki/](http://www.thinkwiki.org/wiki/)) gives a long description on how to do this.

[COLOR="Blue"][SIZE="4"]**Solution**[/SIZE][/COLOR]
I then looked in *man acpid* and in **/var/log/acpid**. It seems, by default acpi runs the following two scripts:

[B]Suspend to RAM: /etc/acpi/sleepbtn.sh
Suspend to disk: /etc/acpi/hibernatebtn.sh[/B]

They does not make what they are supposed to somehow, but hibernate.sh and sleep.sh works (se above).
So, renaming those two and then symlinking them to hibernate.sh and sleep.sh instead just works :-)
Code :

[INDENT][I]mv /etc/acpi/hibernatebtn.sh /etc/acpi/hibernatebtn.sh-unchanged
    mv /etc/acpi/sleepbtn.sh /etc/acpi/sleepbtn.sh-unchanged
    ln -s /etc/acpi/sleep.sh /etc/acpi/sleepbtn.sh
    ln -s /etc/acpi/hibernate.sh /etc/acpi/hibernatebtn.sh[/I][/INDENT]

Now Fn+F4 and Fn+F12 calls those scripts instead. 
The same perhaps also applies to the menue options in Klaptop, but since I still can not log in I don't know yet.

[COLOR="Blue"][SIZE="4"]**Kdesktop_lock**[/SIZE][/COLOR]
Then my second problem; it has a bug report:
    [http://bugs.kde.org/show_bug.cgi?id=126728](http://bugs.kde.org/show_bug.cgi?id=126728)

Kdesktopt_lock is preventing me form logging in again if I lock my screen, or uses hibernatin/sleep. But by going to a shell (Ctrl+Alt+F1) and, as root do

[INDENT]*    killall kdekstop_lock*[/INDENT]

I am able to be back where I left. Suspend to RAM then eems to do what it's supposed to, also from this menue, but suspend to disk just does exactly the same. Now where did hibernate go?

[INDENT]*    klaptop_acpi_helper --hibernate*[/INDENT]
and
[INDENT]*    klaptop_acpi_helper --suspend*[/INDENT]

says: Can't find /usr/sbin/pmi 

[INDENT]*    klaptop_acpi_helper --standby*[/INDENT]

does nothing, says nothing.

[INDENT]*    klaptop_acpi_helper --software-suspend*[/INDENT]

says: Can't find /usr/sbin/hibernate

I will have to take a closer look at this later, for now I can at least use the buttons, the menu I just will have to leave untouched until the mentioned KDE bug is solved, then both options will give me sleep--or maybe someone has fixed that too by then :-P

---

