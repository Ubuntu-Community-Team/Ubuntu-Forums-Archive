---
title: "Keyboard doesn't at first startup."
date: 2010-04-19
forum: General Help
---

### Post by __Sun__ on 2010-04-19
Greetings, everyone.

[SOLVED]
Problem one: My keyboard wasn't working.
Solution one: Needed a new xorg.conf file.

Problem two: How to open a programme in terminal without rendering the terminal unresponsive until that programme is closed.
Solution two: Append a '&' at the end of the command. For example: gedit test-file &
[/SOLVED]

I am a very new Ubuntu user. So far the experience has been pleasant save for one thing: **the keyboard.**

The problem is, my keyboard doesn't respond when I first boot into Ubuntu. None of the keys seem to work except the 'power' key (which helps me turn this laptop on or off).
During the second boot, I incessantly press the space bar hoping for something to happen.
Only when the boot process completes and I see my desktop does the keyboard, finally, respond.
That is precisely how I'm typing this very moment. I had not faced this problem on Windows. I use a laptop (an old one but not too old).

Nothing happens during the first boot regardless the key I press on any time.
It is a nuisance to restart my laptop and periodically strain my space bar for the keyboard to respond on the second boot (It refuses to respond on the first boot, regardless of what I do).

Well, I would really be glad if someone could assist me. I am absolutely dumbfounded, having never faced this particular problem on Windows.

If I might be allowed to, I would like to request for one more answer. When I, sometimes, open files using *gedit* through terminal by typing: **~$ gedit PATH**, what happens is that I am then unable to use any other commands on the same terminal until I close *gedit* or open another terminal.
I can type in the terminal but nothing happens until I exit *gedit*.
I would like my terminal to be responsive whilst I am working on *gedit* simultaneously. I hope it is not impossible...

Would any of you kind people know what I must do?

Hoping for an informative reply. Be easy, for I am quite new to Ubuntu.

-Sun

---

### Post by klemes on 2010-04-19
For the second part of your post the answer is easy.This is normal behavior.If you wish to type some more commands open a new terminal or a new tab in the existing terminal.
You can have any number of open terminals in Linux....

For the keyboard part I am afraid there is no easy answer.Your mouse works at the first boot or only the keyboard is not responding?Do you have an xorg.conf file in the /etc/X11/ directory?If you have you must provide us with this in order for someone to try to be of some help.

One thing you might try is edit /etc/X11/xorg.conf file if you have one and look for the ServerLayout section.There add the following line:

```
Option "AllowEmptyInput"  "off"
```

Also in a terminal type dmesg |grep hal and  dmesg |grep dbus and look for any errors or any unusual outputs.....

---

### Post by arubislander on 2010-04-19
Another answer to the second question is to use 
```
~$ gedit some-file.txt &
```

By adding an ampersand at the end of the command you signal the terminal to start it in the background. In that way you can continue to use the terminal.

---

### Post by linden940 on 2010-04-19
looks like you have the help that you need...just going to say this tho

you posted to problems in ONE post..that's ok this time but if you do that alot sometimes the one problem that you asked wont be addressed because it could be "for gotin" so as a rule of thumb...best to post each problem in one post

and after you find the fix...post it as solved and HOW it was solved for other readers (the few who use the search)

and welcome to the forums hope you like it here and that we can be of help

---

### Post by __Sun__ on 2010-04-19
> **klemes]
For the second part of your post the answer is easy.This is normal behavior.If you wish to type some more commands open a new terminal or a new tab in the existing terminal.
You can have any number of open terminals in Linux....

For the keyboard part I am afraid there is no easy answer.Your mouse works at the first boot or only the keyboard is not responding?Do you have an xorg.conf file in the /etc/X11/ directory?If you have you must provide us with this in order for someone to try to be of some help.

One thing you might try is edit /etc/X11/xorg.conf file if you have one and look for the ServerLayout section.There add the following line:

     Code:
     Option "AllowEmptyInput"  "off" 
Also in a terminal type dmesg |grep hal and  dmesg |grep dbus and look for any errors or any unusual outputs.....     [/QUOTE]

My mouse works, and the power button. The rest of the laptop's keyboard doesn't respond.
Hmm,  it seems, sadly, that there is no such file as **xorg.conf** in my /etc/X11/ directory.
Is that the root of the problem?

As for the last two commands you specified, this is the output:

```
sun@sun-laptop:/$ dmesg |grep hal
[    1.080652] Marking TSC unstable due to TSC halts in idle
sun@sun-laptop:/$ dmesg |grep dbus
[   18.338550] yenta_cardbus 0000:05:04.0: CardBus bridge found [17aa:3828]
[   18.338580] yenta_cardbus 0000:05:04.0: Using CSCINT to route CSC interrupts to PCI
[   18.338583] yenta_cardbus 0000:05:04.0: Routing CardBus interrupts to PCI
[   18.338590] yenta_cardbus 0000:05:04.0: TI: mfunc 0x01111c12, devctl 0x44
[   18.616816] yenta_cardbus 0000:05:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   18.616822] yenta_cardbus 0000:05:04.0: Socket status: 30000006
[   18.616837] yenta_cardbus 0000:05:04.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   18.617097] yenta_cardbus 0000:05:04.0: pcmcia: parent PCI bridge Memory window: 0xd4100000 - 0xd41fffff
[   18.617101] yenta_cardbus 0000:05:04.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
```I have little to no idea what that output is supposed to imply. But, can this message be considered as a warning:
```
[    1.080652] Marking TSC unstable due to TSC halts in idle
```And I seem to lack the *xorg.conf* file you specified earlier.
Is it supposed to be an important file?
When I searched for '*xorg.conf*' using the search option all I found was a file namely **xorg.conf.5.gz **which I believe is a GNU Zip file. Inside this zip was a '*xorg.conf.5' *file with lots of what seemed like various file paths and some code.

Shall I post the contents of this *xorg.conf.5*? Please, do assist me here.

[QUOTE=arubislander said:**
> Another answer to the second question is to use 
```
~$ gedit some-file.txt &
```By adding an ampersand at the end of the command you signal the terminal to start it in the background. In that way you can continue to use the terminal.

Ah, much obliged. That worked perfectly! Now, only the keyboard problem remains.

[QUOTE=linden940]looks like you have the help that you need...just going to say this tho

you posted to problems in ONE post..that's ok this time but if you do that alot sometimes the one problem that you asked wont be addressed because it could be "for gotin" so as a rule of thumb...best to post each problem in one post

and after you find the fix...post it as solved and HOW it was solved for other readers (the few who use the search)

and welcome to the forums hope you like it here and that we can be of help[/QUOTE]

It appears that you are correct. My keyboard problem persists still. It doesn't work when I first start this laptop but fortunately I have one less problem to worry about. Nevertheless, I shall follow your kind advice for my future posts (or threads). I'll remember to change the prefix to [SOLVED] when my former question is relieved with an answer, that time is yet to come.

If anyone does know of a solution to the first problem I'd be elated to hear it (or rather, read it on my screen).

---

### Post by klemes on 2010-04-19
Sorry not exactly what was looking for....my mistake....

Could you try these two commands and paste the output??

#ps aux |grep hal

#ps aux |grep dbus

---

### Post by __Sun__ on 2010-04-20
> **klemes said:**
> Sorry not exactly what was looking for....my mistake....

Could you try these two commands and paste the output??

#ps aux |grep hal

#ps aux |grep dbus

I am at your mercy:

```

eshwar@eshwar-laptop:~$ ps aux |grep hal
107        833  0.0  0.4   6264  4136 ?        Ss   07:27   0:03 hald --daemon=yes
root       926  0.0  0.1   3344  1204 ?        S    07:27   0:00 hald-runner
root      1068  0.0  0.1   3416  1116 ?        S    07:27   0:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      1082  0.0  0.1   3412  1136 ?        S    07:27   0:00 /usr/lib/hal/hald-addon-generic-backlight
root      1093  0.0  0.1   3420  1136 ?        S    07:27   0:01 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1096  0.0  0.1   3420  1144 ?        S    07:27   0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3 /dev/input/event2 /dev/input/event6 /dev/input/event5 /dev/input/event9
root      1101  0.0  0.1   3428  1128 ?        S    07:27   0:00 /usr/lib/hal/hald-addon-cpufreq
107       1102  0.0  0.1   3264  1136 ?        S    07:27   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
eshwar    4949  0.0  0.0   3044   848 pts/0    S+   09:45   0:00 grep --color=auto hal
eshwar@eshwar-laptop:~$ ps aux |grep dbus
102        790  0.0  0.1   3168  1544 ?        Ss   07:27   0:07 dbus-daemon --system --fork
eshwar    1546  0.0  0.0   4712   604 ?        Ss   07:27   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
eshwar    1549  0.0  0.0   3384   720 ?        S    07:27   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
eshwar    1550  0.0  0.1   3108  1456 ?        Ss   07:27   0:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
eshwar    4951  0.0  0.0   3044   844 pts/0    S+   09:46   0:00 grep --color=auto dbus

```How might you interpret this output?
So I may take that this **xorg.conf** file is not important enough since you did not mention anything regarding it in your last post.

Well, there is not much I can do to help myself.
What am I to do next, sir?

---

### Post by __Sun__ on 2010-04-23
So this is the way I am treated.
Will I get a reply or not?

---

### Post by klemes on 2010-04-23
> **__Sun__ said:**
> I am at your mercy:

```

eshwar@eshwar-laptop:~$ ps aux |grep hal
107        833  0.0  0.4   6264  4136 ?        Ss   07:27   0:03 hald --daemon=yes
root       926  0.0  0.1   3344  1204 ?        S    07:27   0:00 hald-runner
root      1068  0.0  0.1   3416  1116 ?        S    07:27   0:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      1082  0.0  0.1   3412  1136 ?        S    07:27   0:00 /usr/lib/hal/hald-addon-generic-backlight
root      1093  0.0  0.1   3420  1136 ?        S    07:27   0:01 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1096  0.0  0.1   3420  1144 ?        S    07:27   0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3 /dev/input/event2 /dev/input/event6 /dev/input/event5 /dev/input/event9
root      1101  0.0  0.1   3428  1128 ?        S    07:27   0:00 /usr/lib/hal/hald-addon-cpufreq
107       1102  0.0  0.1   3264  1136 ?        S    07:27   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
eshwar    4949  0.0  0.0   3044   848 pts/0    S+   09:45   0:00 grep --color=auto hal
eshwar@eshwar-laptop:~$ ps aux |grep dbus
102        790  0.0  0.1   3168  1544 ?        Ss   07:27   0:07 dbus-daemon --system --fork
eshwar    1546  0.0  0.0   4712   604 ?        Ss   07:27   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
eshwar    1549  0.0  0.0   3384   720 ?        S    07:27   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
eshwar    1550  0.0  0.1   3108  1456 ?        Ss   07:27   0:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
eshwar    4951  0.0  0.0   3044   844 pts/0    S+   09:46   0:00 grep --color=auto dbus

```How might you interpret this output?
So I may take that this **xorg.conf** file is not important enough since you did not mention anything regarding it in your last post.

Well, there is not much I can do to help myself.
What am I to do next, sir?

Well I can see no problem there...
> **__Sun__ said:**
> So this is the way I am treated.
Will I get a reply or not?

give me a while I will try to review your first post ...it's been a while and I do not remember your problem originally...
PS you have been more than patient  .you know most users use bump or something similar a lot earlier than three days from the time of the first post.But keep in mind that we are only volunteers and that there is nowhere implied any guaranteed results or outcome.

---

### Post by klemes on 2010-04-23
So you do not have a xorg.conf....hmmm...

Let's make one by switching into a terminal by pressing CTRL+Alt+F2
then we give our credentials and hopefully then we are logged-in
Then we type at the prompt:

```
sudo X -configure 
```

and after that:

```
sudo X -config  ~/xorg.conf.new
```

so to test the new X server.

If the test is successful and you get an X server up and running then and ONLY THEN  proceed with the following in order to make changes permanent:

```
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
```

and then reboot to test your keyboard:

```
sudo reboot
```

---

### Post by __Sun__ on 2010-04-25
> **klemes said:**
> So you do not have a xorg.conf....hmmm...

Let's make one by switching into a terminal by pressing CTRL+Alt+F2
then we give our credentials and hopefully then we are logged-in
Then we type at the prompt:

```
sudo X -configure 
```and after that:

```
sudo X -config  ~/xorg.conf.new
```so to test the new X server.

If the test is successful and you get an X server up and running then and ONLY THEN  proceed with the following in order to make changes permanent:

```
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
```and then reboot to test your keyboard:

```
sudo reboot
```

OK, this may be a bit embarrassing for me to ask but, when I do press CTRL+ALT+F2 I see a command prompt which asks me to login, it looks something like this:
```
eshwar@eshwar-laptop login: 
```When I do enter my password and press the return key, after a few seconds I get an 'incorrect' message. I tried my root password after setting it by using the 'sudo passwd' command (I read that elsewhere around in the forums... does it really set my root password?) but I still got that 'incorrect password' message.
I know I'm typing the right password, for I typed it more than 10 times.
After typing 5 times I receive a message claiming something along these lines: 'Max 5 tries' (not exactly this message but something similar, I cannot recall sharply).
But it still inevitably asked for a password and waited for input.

One thing I found was that it waited several seconds to output after I pressed the return key - which seems odd, my terminal doesn't wait even if I input a wrong password.
It may be nothing.

I 'am once again dumbfounded as to why I'm getting a login screen when I 'am already logged on reading this very thread on this very forum. And why was the password I always use being rejected.

Typing anything was useless, because after hitting enter it inexorably asks for a 'Password: '.

So, I ask you, is this normal?

I almost feel helpless.

---

### Post by klemes on 2010-04-25
No it's not normal....
But you can still login as root if I understand correct....
So login as root and change your  _**user**_ password:

#passwd your_username

it will prompt you twice for a new password give the new (or the same )password and then 
logout as root and login again as user this time then carry on with the commands I wrote you about in the previous post.

See you in a couple of days I guess it seems you respond every other day or so....)....:P:guitar:

---

### Post by fragos on 2010-04-26
I just upgraded to a new motherboard and find keyboard input to get into the BIOS or to respond to Grub is inconsistent. Sometime yes but mostly no. The keyboard always works once X is started. It's manageable since I rarely if ever have to do BIOS setup after the 1st time and Grub has a timer so the boot to X happens automatically. My motherboard is an Asrock and since the issue happens in both BIOS and Grub I'd think it's a hardware implementation issue but am only guessing.

---

### Post by __Sun__ on 2010-04-26
Well, I got past that stupid problem, but got this one instead:

```

eshwar@eshwar-laptop:~$ sudo X -configure
[sudo] password for eshwar: 

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
eshwar@eshwar-laptop:~$ 

```

Sigh, I do not know how to properly remove that particular .X0-lock file.
Am I to just delete or rename it, I hope it wouldn't cause other errors.

One problem after the other eh?
Really really bad luck.

---

### Post by klemes on 2010-04-26
Well before you execute the X -configure command give:

```
sudo /etc/init.d/gdm stop
```

This means you will be stuck in terminal mode without X temporarily.

After yoiu finished testing the new xorg file and you are ready to go back to X type:

```
sudo /etc/init.d/gdm start
```

Good Luck!!!!:guitar:

---

### Post by __Sun__ on 2010-04-26
Well, I went all the way up to the "sudo X -config ~/xorg.conf.new" command.

But, after that all I see is a blank screen, no success message, no failure message.
I pressed CTRL+ALT+F7 but nothing happened. I pressed CTRL+ALT+F2 and I was taken back to the terminal where I was asked to login again.

Pressing CTRL+ALT+F7 took me back the the blank screen.
Well, I tried the same process again but I got the 'server display already 0' message.

So, is this blank screen an indicator of success or failure?

Here is my xorg.conf.new:
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "dri2"
    Load  "record"
    Load  "glx"
    Load  "extmod"
    Load  "dri"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```Well, do reply, I still have zero clue as to what all that code does.

EDIT: Problem solved!

Thanks a lot for your patience and guidance klemes, really man, thanks a bunch.
It works now. It actually works without having to restart.

---

### Post by klemes on 2010-04-26
Now all that remains is to move your ~/xorg.conf.new to the correct location and that would be /etc/X11 so type this two commands logged-in as a user:

A.```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```  # This command backups your existing xorg.conf if tehre is already one.

B.```
sudo cp ~/xorg.conf.new /etc/X11/xorg.conf
``` # this actually copies the xorg.conf.new to it's new position

Be careful when typing and remember [TAB] completion is your friend when typing in a terminal or console....


After that reboot and see if that eliminates your problem.If not we will think of something....:popcorn:
:guitar:

---

### Post by __Sun__ on 2010-04-27
Thanks, I already copied the 'xorg.conf.new' to /etc/X11 as 'xorg.conf'.
Now the keyboard works even if it is running on battery and I don't have to restart.

Making a backup is a good idea - I just did that as well (copied it as 'xorg.conf.bak' at another directory).

Thanks again for your kind patience and help.
I'll pester you if I have any more problems with my Ubuntu, if you don't mind, haha.

Have a nice day. ):P

---

