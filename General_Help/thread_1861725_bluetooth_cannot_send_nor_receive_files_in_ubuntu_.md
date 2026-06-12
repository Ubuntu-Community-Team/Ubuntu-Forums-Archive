---
title: "bluetooth cannot send nor receive files in ubuntu 11.10"
date: 2011-10-15
forum: General Help
---

### Post by Jordanbadangayon on 2011-10-15
Hello Ubuntu folks. I just got a problem with Oneiric. My bluetooth, which worked perfectly in Natty, suddenly has gone crazy. It seems to be unable to receive or send files. After pairing my computer with my phone, I clicked 'browse files' but nothing happened (in Natty, it used to open nautilus and browse files from my phone). I tried sending a file but failed. It says 'did not receive a reply'. I tried sending a file from my phone to my computer but also failed. Did anyone encounter this problem?? Please help... :confused: . I don't know if it's a driver problem or anything but it worked perfectly in Natty so I guess it has to do something with Oneiric. 
BTW, I have a Vaio-VPCCW1S1E running Ubuntu 11.10. I just upgraded yesterday. 
Thanks.

---

### Post by jimmyxu on 2011-10-16
I had the same problems.  -_-

---

### Post by khurtsiya on 2011-10-16
same here

where is the menu item "Receive files" where I can opt to receive from all devices?

---

### Post by alcantor on 2011-10-17
I've got 'DBus error' while trying browsing my bluetooth phone too :(

---

### Post by justin_wzy on 2011-10-18
Same here... the error msg says "Unable to find service record"

---

### Post by Saladin1 on 2011-10-18
me too have the same problem, cannot receive from my android smartphone

---

### Post by Hrimfaxi on 2011-10-19
> **alcantor said:**
> I've got 'DBus error' while trying browsing my bluetooth phone too :(

I also receive this error. Everything worked fine before the upgrade from 11.04. I can only send files to the phone now.

---

### Post by Jordanbadangayon on 2011-10-19
After an update, I am now able to receive files from my phone via bluetooth but I still can't send anything. :(

---

### Post by madsjuul on 2011-10-20
I have same problem I get this message

Could not display "obex//:[00:23:F1: 06:F1:C0]/"
Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again.

:-(

---

### Post by eltntawy on 2011-10-20
same problem toooooooooooooooooooooo. please find solution quickly :(

---

### Post by Jordanbadangayon on 2011-10-21
> **khurtsiya said:**
> same here

where is the menu item "Receive files" where I can opt to receive from all devices?

Try opening 'personal file sharing' from dash...

---

### Post by apoapo on 2011-10-22
Same here. I reported a bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/879923](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/879923)

You may want to raise the heat with clicking "this bug affects me" or even add more information to the report.

Thanks

apo

---

### Post by Vyodacoda on 2011-10-23
I also have the same but there is more
1) Browse Files on device no longer works
2) Send Files no longer works
3) It does not show an Icon on the desktop to show that the device is connected
4) Sync via Bluetooth no longer works
5) I Tried Blueman which managed to send files ok but when I exited Blueman the desktop was blown away leaving just the Desktop Background ( Wallpaper ) with no icons and the machine hung. 
I have 2 Dual boot machines with 11.04 and 11.10 both with different Bluetooth adaptors, 11.04 still works on both.

---

### Post by gagmani on 2011-10-23
i got it , it is bug in new linux kernel 3.x.I had linux mint 11(ubuntu 11.04 natty based).I upgraded linux kernel to 3.1 from 2.6 and same problems as ubuntu 11.10 emerged.So until there is bug fix by ubuntu or linux kernel developers,I would stick to 11.04 or linux mint.By the way, I have a pc with external siliconwave dongle, does not work at all.I also have a Vaio VPCEB34/en ,same problems as you have,Jordanbadangayon.

---

### Post by sarv_jeet on 2011-10-24
I also have the same problem. Even after updating bluez problem persists .

---

### Post by saliflo on 2011-10-24
solved with update

---

### Post by khurtsiya on 2011-10-25
nothing solved here
windoze works perfectly (meaning blutooth) on same machine

---

### Post by madsjuul on 2011-10-25
Nothing solved here

---

### Post by markdark20 on 2011-10-25
> **Jordanbadangayon said:**
> Try opening 'personal file sharing' from dash...

Solved. Thanks :popcorn:

---

### Post by khurtsiya on 2011-10-25
> **Jordanbadangayon said:**
> Try opening 'personal file sharing' from dash...

That solved the problem! Thanks!

---

### Post by joserobleda on 2011-10-27
Same problem here. And enabling file share doesnt work.

---

### Post by typhoon_tip on 2011-10-27
> **saliflo said:**
> solved with update

Have you upgraded Kernel to 3.0.13 from the Ubuntu proposed reps ?

---

### Post by B Crowther on 2011-10-28
I have enabled file sharing via the dash.
I have updated the kernel via "proposed".
I can pair the phone and the computer via the bluetooth applet.
I can now receive files from my phone.
My phone can't browse the computer.
My computer can't browse the phone, if I try to, the bluetooth applet disappears, and "unity --replace all" doesn't bring it back, although the bluetooth is still running....somewhere.
My computer can't send files to the phone (Permission denied (13) is the message I get.)
Wammu can't find my phone (Actually, Wammu can't find it via usb, either, another thing apparently broken since 11.04!).
Why do Ubuntu break bluetooth with each new version?
Do I have to go back to 11.04 with both computers?

P.s. I also tried adding my name to the bluetooth user group (and they have made that a further complication in 11.10, you have to do it through the terminal now, no more "Users and Groups"), made no difference.

---

### Post by joserobleda on 2011-10-28
I have upgrade the kernel to the proposed version and enable personal file sharing but nothing, problem still here...

¿Any other ideas?

---

### Post by sampathkuma on 2011-10-29
> **Jordanbadangayon said:**
> Try opening 'personal file sharing' from dash...
Thanks. Solved my problem of sending from mobile to Ubuntu 11.10.

---

### Post by RedRoss on 2011-10-29
Something similar here. Paired my phone,  it seems to detect OK. The phone asks if it should allow data transfer when I click 'browse files' on my laptop. But nothing happens.


Though I can send files through bluetooth to the phone.

---

### Post by Hrimfaxi on 2011-10-29
Still unable to browse files. Any other suggestions on a fix?

Also the error I'm getting is:
> Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again.

---

### Post by oldtimer7777 on 2011-10-29
> **Hrimfaxi said:**
> Still unable to browse files. Any other suggestions on a fix?

Also the error I'm getting is:

Did you check to see if it is working on a live stick of Ubuntu 10.10?  Just for comparison?

---

### Post by Hrimfaxi on 2011-10-29
> **oldtimer7777 said:**
> Did you check to see if it is working on a live stick of Ubuntu 10.10?  Just for comparison?

Yes. It works great under 10.10 and 11.04.

---

### Post by rimibchatterjee on 2011-11-01
I just installed Ubuntu 11.10 Oneiric Ocelot on my Lenovo G560 laptop yesterday. I too can't receive or send files with bluetooth. When I hit connect on my phone with the bluetooth dialogue window open, the slider next to Connection flashes ON for a microsecond (but does not turn orange) then falshes OFF (both grey) I then get the message connecting failed/retry on my phone.
This may be a stupid question, but how do I access personal file sharing from the dash?:confused:

---

### Post by Jordanbadangayon on 2011-11-02
> **rimibchatterjee said:**
> I just installed Ubuntu 11.10 Oneiric Ocelot on my Lenovo G560 laptop yesterday. I too can't receive or send files with bluetooth. When I hit connect on my phone with the bluetooth dialogue window open, the slider next to Connection flashes ON for a microsecond (but does not turn orange) then falshes OFF (both grey) I then get the message connecting failed/retry on my phone.
This may be a stupid question, but how do I access personal file sharing from the dash?:confused:
Hit the super/windows key to open dash (you can also do this by clicking the icon with the Ubuntu logo on it on the launcher) then type 'personal file sharing' in the search box. :D.

---

### Post by rimibchatterjee on 2011-11-02
Worked like a charm. Thanks Jordanbadangayon:KS

---

### Post by vangop on 2011-11-05
> **B Crowther said:**
> I have enabled file sharing via the dash.
I have updated the kernel via "proposed".
I can pair the phone and the computer via the bluetooth applet.
I can now receive files from my phone.
My phone can't browse the computer.
My computer can't browse the phone, if I try to, the bluetooth applet disappears, and "unity --replace all" doesn't bring it back, although the bluetooth is still running....somewhere.
My computer can't send files to the phone (Permission denied (13) is the message I get.)
Wammu can't find my phone (Actually, Wammu can't find it via usb, either, another thing apparently broken since 11.04!).
Why do Ubuntu break bluetooth with each new version?
Do I have to go back to 11.04 with both computers?

P.s. I also tried adding my name to the bluetooth user group (and they have made that a further complication in 11.10, you have to do it through the terminal now, no more "Users and Groups"), made no difference.

For those who "did everything" but can't send files due to "permission denied" - [mount the phone]("http://ubuntu-answers.blogspot.com/2011/11/bluetooth-on-ubuntu-1110.html") and just copy the files.

---

### Post by techvish81 on 2011-11-05
unacceptable,  Bluetooth has now become an undeniable requirement , it should have to be fixed very soon,  

has anyone tried it in other 'buntus'?

---

### Post by seapaladin on 2011-11-05
Ubuntu 11.10 all updates done (including pre-released-updates)  , personal file sharing activated ( it complain about missing packages an y found the solution on google , install apache2.2-bin and libapache2-mod-dnssd  ) and still "browse files" function not functional from nautilus . From terminal it works for me using this commands 
"obexfs -b PUT-HERE-YOUR-DEVICE-ADDRES ~/nokia " (to mount my e90 )
"fusermount --u ~/nokia" (unmount my device )
hope this help someone

---

### Post by Scoobin on 2011-11-06
> **seapaladin said:**
> Ubuntu 11.10 all updates done (including pre-released-updates)  , personal file sharing activated ( it complain about missing packages an y found the solution on google , install apache2.2-bin and libapache2-mod-dnssd  ) and still "browse files" function not functional from nautilus . From terminal it works for me using this commands 
"obexfs -b PUT-HERE-YOUR-DEVICE-ADDRES ~/nokia " (to mount my e90 )
"fusermount --u ~/nokia" (unmount my device )
hope this help someone

Seapaladin, where you say address there to you mean MAC or IP or something else?

---

### Post by vangop on 2011-11-06
It's MAC. [Instructions]("http://ubuntu-answers.blogspot.com/2011/11/bluetooth-on-ubuntu-1110.html").

---

### Post by Joleen on 2011-11-09
> **seapaladin said:**
> Ubuntu 11.10 all updates done (including pre-released-updates)  , personal file sharing activated ( it complain about missing packages an y found the solution on google , install apache2.2-bin and libapache2-mod-dnssd  ) and still "browse files" function not functional from nautilus . From terminal it works for me using this commands 
"obexfs -b PUT-HERE-YOUR-DEVICE-ADDRES ~/nokia " (to mount my e90 )
"fusermount --u ~/nokia" (unmount my device )
hope this help someone
   



THAKS a lot! hcitool command did not work for me, but obexfs -b etc did the job! 
:KS:KS:KS:KS:KS

---

### Post by Joleen on 2011-11-09
> **Joleen said:**
> THAKS a lot! hcitool command did not work for me, but obexfs -b etc did the job! 
:KS:KS:KS:KS:KS
  (people that requires previous installation of obexfs: 
[B]sudo apt-get install obexfs  )
[/B]

---

### Post by CaptainMark on 2011-11-12
ive had a [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/872044") going for those people who are still getting the permission denied error when sending files

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/872044](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/872044)

---

### Post by Daniel TL on 2011-11-14
> **vangop said:**
> For those who "did everything" but can't send files due to "permission denied" - [mount the phone]("http://ubuntu-answers.blogspot.com/2011/11/bluetooth-on-ubuntu-1110.html") and just copy the files.

Thank you!! It's work fine for me! :)

---

### Post by evertmantel on 2011-11-21
> **Jordanbadangayon said:**
> Hit the super/windows key to open dash (you can also do this by clicking the icon with the Ubuntu logo on it on the launcher) then type 'personal file sharing' in the search box. :D.

Did the trick!

---

### Post by saliflo on 2011-11-21
If personal file sharing doesn't work, install libgnome frome synaptic.

---

### Post by vatzec on 2011-11-22
Please mark it as solved, so others will know they can find a solution here. :)

---

### Post by Atcold on 2011-11-23
I did the following (the first only once):
```
sudo apt-get install obexfs
```
So:
```
hcitool scan
```
then I copied the MAC, say, FF:FF:FF:FF:FF:FF, and created a new directiory, say, *MyPhone* in *Home*, thus
```
obexfs -b FF:FF:FF:FF:FF:FF ~/MyPhone
```
and after, to unmount:
```
fusermount -u ~/MyPhone
```
But it is excessively slow. Browsing the content takes ages! And it becomes even worse when I attempt to download a file from the phone to the PC.

BTW, the setting *Receive Files over Bluetooth* from the *Personal File Sharing Preferences* does not do the work, i.e. I still cannot send files from my phone to Ubuntu 11.10 (even if I can the the other way around, i.e. sending files from the PC to the phone).

So, what are the next steps folks? Every suggestion is well appreciated!
Thanks

---

### Post by CaptainMark on 2011-11-24
there is a patch thats been uploaded onto launchpad, all you can do is wait and hope the devs of this package check it and included it in the updates,

---

### Post by Atcold on 2011-11-24
> **CaptainMark said:**
> there is a patch thats been uploaded onto launchpad, all you can do is wait and hope the devs of this package check it and included it in the updates,
Well, is this *patch* already working, or has just been ask *Launchpad* to make a *patch* to solve the problem?
Thanks

---

### Post by CaptainMark on 2011-11-24
i havent tried the patch, heres the bug report [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/872044](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/872044) i wouldnt know how to test the patch

---

### Post by vangop on 2011-11-25
> **Atcold said:**
> I did the following (the first only once):

BTW, the setting *Receive Files over Bluetooth* from the *Personal File Sharing Preferences* does not do the work, i.e. I still cannot send files from my phone to Ubuntu 11.10 (even if I can the the other way around, i.e. sending files from the PC to the phone).

So, what are the next steps folks? Every suggestion is well appreciated!
Thanks

What kind of error do u get when sending a file from the phone?

---

### Post by Atcold on 2011-11-26
> **CaptainMark said:**
> i havent tried the patch, heres the bug report [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/872044](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/872044) i wouldnt know how to test the patch
I see.
> **vangop said:**
> What kind of error do u get when sending a file from the phone?
When I attempt to send a file from the phone, it replies with the following *ERROR*:
```
Cannot connect to the OBEX device.
It is either not accessible or does not support selected service.
```
And it gives me also an *Action Failed* notification:
```
Cannot copy the file 'file_name'. The remote system refused the network connection.
```
Whereas Ubuntu (11.10) does not even notify any kind of warning or error.


Anyway, installing *obexfs*, now I've got two icons. The former did/does not pair with the phone, whereas the latter does. Anyway, it allows me only to send (and not receive) files to the phone.

[CENTER][IMG]http://img267.imageshack.us/img267/1407/screenshotat20111125123.png[/IMG][/CENTER]

---

### Post by kanhiya on 2011-11-26
Here is a temporary fix, 

[http://ubuntu.igameilive.com/2011/11/temporary-problematic-bluetooth-fix-in.html](http://ubuntu.igameilive.com/2011/11/temporary-problematic-bluetooth-fix-in.html)

,I am also having same problem, I am not satisfied a bit from Ubuntu 11.10, worst release , i have ever seen from Canonical.

Simple device like bluetooth which is of daily use & were working well in previous distro & they are saying that We are improving, getting better
:(, thumbs down to canonical.


:(

---

### Post by Atcold on 2011-11-27
> **kanhiya said:**
> Here is a temporary fix, 

[http://ubuntu.igameilive.com/2011/11/temporary-problematic-bluetooth-fix-in.html](http://ubuntu.igameilive.com/2011/11/temporary-problematic-bluetooth-fix-in.html)

,I am also having same problem, I am not satisfied a bit from Ubuntu 11.10, worst release , i have ever seen from Canonical.

Simple device like bluetooth which is of daily use & were working well in previous distro & they are saying that We are improving, getting better
:(, thumbs down to canonical.


:(
It's just what I suggested in post [45]("http://ubuntuforums.org/showpost.php?p=11484274&postcount=45"), which was inspired from [this]("http://ubuntu-answers.blogspot.com/2011/11/bluetooth-on-ubuntu-1110.html").

---

### Post by vangop on 2011-11-30
[LIST=1]
[/LIST]> **Atcold said:**
> I see.

When I attempt to send a file from the phone, it replies with the following *ERROR*:
```
Cannot connect to the OBEX device.
It is either not accessible or does not support selected service.
```
And it gives me also an *Action Failed* notification:
```
Cannot copy the file 'file_name'. The remote system refused the network connection.
```
Whereas Ubuntu (11.10) does not even notify any kind of warning or error.


Anyway, installing *obexfs*, now I've got two icons. The former did/does not pair with the phone, whereas the latter does. Anyway, it allows me only to send (and not receive) files to the phone.

Hmm, it's interesting since it lets you send to the phone.
Can you check the about dialog of both icons? (what app that is)
Also can you check what BT libs you've got
```
% sudo dpkg -l |grep bluet
```
Regarding the receive error - can you check your syslog for any hints?
```
% tail /var/log/syslog
```

---

### Post by Atcold on 2011-11-30
> **vangop said:**
> [LIST=1]
[/LIST]
Hmm, it's interesting since it lets you send to the phone.
Can you check the about dialog of both icons? (what app that is)
The one that does pair is the following:

[CENTER][IMG]http://img265.imageshack.us/img265/9471/newbtapp.png[/IMG][/CENTER]
The other is just the *standard* pre-installed one.
> Also can you check what BT libs you've got
```
% sudo dpkg -l |grep bluet
```
```
atcold@atcold-Pavilion-dv7:~$ sudo dpkg -l | grep bluet
[sudo] password for atcold: 
ii  blueman                                1.23+r731~oneiric1                      A Graphical bluetooth manager
ii  gir1.2-gnomebluetooth-1.0              3.2.0-0ubuntu2                          Introspection data for GnomeBluetooth
ii  gnome-bluetooth                        3.2.0-0ubuntu2                          GNOME Bluetooth tools
ii  libbluetooth3                          4.96-0ubuntu4                           Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth8                    3.2.0-0ubuntu2                          GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth            1:1.0-0ubuntu3.1                        Bluetooth module for PulseAudio sound server

```
> Regarding the receive error - can you check your syslog for any hints?
```
% tail /var/log/syslog
```
```
atcold@atcold-Pavilion-dv7:~$ tail /var/log/syslog
Nov 30 12:19:26 atcold-Pavilion-dv7 avahi-daemon[966]: Invalid response packet from host fe80::42a6:d9ff:fe9f:7f69.
Nov 30 12:20:27  avahi-daemon[966]: last message repeated 3 times
Nov 30 12:21:16 atcold-Pavilion-dv7 wpa_supplicant[1110]: WPA: Group rekeying completed with 00:1e:13:c6:cf:31 [GTK=TKIP]
Nov 30 12:21:18 atcold-Pavilion-dv7 wpa_supplicant[1110]: WPA: Group rekeying completed with 00:1e:13:c6:cf:31 [GTK=TKIP]
Nov 30 12:23:08 atcold-Pavilion-dv7 dhclient: DHCPREQUEST of 140.105.234.232 on eth2 to 172.30.48.2 port 67
Nov 30 12:23:08 atcold-Pavilion-dv7 dhclient: DHCPACK of 140.105.234.232 from 172.30.48.2
Nov 30 12:23:08 atcold-Pavilion-dv7 dhclient: bound to 140.105.234.232 -- renewal in 279 seconds.
Nov 30 12:23:39 atcold-Pavilion-dv7 wpa_supplicant[1110]: WPA: Group rekeying completed with 00:1e:13:c6:cf:31 [GTK=TKIP]
Nov 30 12:24:33 atcold-Pavilion-dv7 wpa_supplicant[1110]: WPA: Group rekeying completed with 00:1e:13:c6:cf:31 [GTK=TKIP]
Nov 30 12:25:29 atcold-Pavilion-dv7 wpa_supplicant[1110]: WPA: Group rekeying completed with 00:1e:13:c6:cf:31 [GTK=TKIP]

```
Anyway, **vangop** thanks for your interest! I am a Linux newbie and I do not know where to put my hands.

---

### Post by vangop on 2011-11-30
Looks like you've got somehow blueman updated to 1.23, which I could only with ppa (11.10 repos have 1.22~bzr707-1ubuntu1).
Was quite excited to try it out. Well yes, the pairing now works from phone, but I still can't send the file from the PC - connection refused.
Although I'm on xubuntu and only have ```
ii  blueman                                  1.23+r731~oneiric1                      A Graphical bluetooth manager
ii  libbluetooth3                            4.96-0ubuntu4                           Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth8                      3.2.0-0ubuntu2                          GNOME Bluetooth tools - support library

```
But you do confirm that now sending the file from PC works?
Regarding your syslog, is it what you get after trying to send the file from the phone?
If it is, you may want to try to run bluetoothd -d = debug mode. It didn't help much for me, the log looked perfectly normal, but still.
if you wanna try - stop the daemon and run it manually with -d.
```
$ sudo service bluetooth stop
$ sudo bluetoothd -d

```
Try to send the file and check the syslog again.

---

### Post by Atcold on 2011-11-30
> **vangop said:**
> Looks like you've got somehow blueman updated to 1.23, which I could only with ppa (11.10 repos have 1.22~bzr707-1ubuntu1).
Pardon?
> But you do confirm that now sending the file from PC works?
It has always worked, also before, even though it did not pair with the phone (no blue symbol).
> Regarding your syslog, is it what you get after trying to send the file from the phone?
I am not following you. I said that Ubuntu does not notify anything. The messages I view are from the phone (Windows Mobile).
> If it is, you may want to try to run bluetoothd -d = debug mode. It didn't help much for me, the log looked perfectly normal, but still.
What should it do?
> Try to send the file and check the syslog again.
OK, I will try.

---

### Post by vangop on 2011-12-01
I'm not sure why my post was so confusing, but what I meant was that we have the opposite problems, PC can receive files but get "connection refused" on send.
Also I suggested to enable debug mode of the bluetooth daemon and check system logs for any hints afterwards.
But now that you've mentioned that you're connecting to Win mobile, I remember I used to have the same [issue]("http://ubuntuforums.org/showthread.php?t=1614788").
Try to receive from a different phone (non win mobile), it should work. Also, I've tried to send/receive to my old win mobile phone from my current 11.10 x64 xubuntu, and it was working EXACTLY the same as for you. So this must be some win mobile interaction issue (win phone->pc), and pc->phone sending fails for android :)
crazy!

---

### Post by 001neeraj on 2011-12-01
The problem is due to the new distribution. I got same problem in Natty. When i had updated, problem was solved. You have to wait until new update for Oneric releases.

---

### Post by Atcold on 2011-12-01
> **vangop said:**
> I'm not sure why my post was so confusing, but what I meant was that we have the opposite problems, PC can receive files but get "connection refused" on send.
Also I suggested to enable debug mode of the bluetooth daemon and check system logs for any hints afterwards.
But now that you've mentioned that you're connecting to Win mobile, I remember I used to have the same [issue]("http://ubuntuforums.org/showthread.php?t=1614788").
Try to receive from a different phone (non win mobile), it should work. Also, I've tried to send/receive to my old win mobile phone from my current 11.10 x64 xubuntu, and it was working EXACTLY the same as for you. So this must be some win mobile interaction issue (win phone->pc), and pc->phone sending fails for android :)
crazy!
Well.. you did not manage to make it work. Nice.. I believe this is one of many factors that will keep me close to Microsoft.

---

### Post by boazjones on 2011-12-05
Same here, I'm afraid.


File Transfer:


"Sending files via Bluetooth" ----> From ----> To:



"Unable to find service record"

---

### Post by CaptainMark on 2011-12-05
bad news, no fix in gnome 3.2, i just tested the opensuse 12.1 gnome live cd and same error, failure

---

### Post by basilwatson on 2011-12-14
Can Confirm, tried a few things , and even with Bluetooth manager , it will crash after a few seconds 

I hope its fixed by the long term LTS version , 

Stephen

---

### Post by Bucic on 2011-12-14
I get either the no reply error or the access denied (13) error. The blueman allows me to send files from my phone to my laptop (Thinkpad T500, Lenovo) but not the other way. In this case which launchpad bug do I subscribe to? I presume there's no easy fix for my case...

---

### Post by jamesbon on 2011-12-15
Please apply following patch and post the results.
[https://bugs.launchpad.net/bugs/872044/+attachment/2623321/+files/obexd.diff](https://bugs.launchpad.net/bugs/872044/+attachment/2623321/+files/obexd.diff)

---

### Post by breaky9973 on 2011-12-22
> **jamesbon said:**
> Please apply following patch and post the results.
[https://bugs.launchpad.net/bugs/872044/+attachment/2623321/+files/obexd.diff](https://bugs.launchpad.net/bugs/872044/+attachment/2623321/+files/obexd.diff)

Coud you please provide a tutorial of some sorts how to apply this patch file?

Thanks.

---

### Post by Atcold on 2011-12-26
> **breaky9973 said:**
> Coud you please provide a tutorial of some sorts how to apply this patch file?

Thanks.
It seems to be sufficient to upgrade to the new kernel (activating the beta version in the packages updater).

---

### Post by cblanquer on 2012-01-15
> **Jordanbadangayon said:**
> Try opening 'personal file sharing' from dash...
THX I was just struggling with the problem, no clue how to set up this as I recently switched form Kubuntu (my platsorm since 2005) to Ubuntu (I love Unity).

---

### Post by ibnYusrat on 2012-01-17
> **Jordanbadangayon said:**
> Try opening 'personal file sharing' from dash...

This [COLOR=SeaGreen]_**solved**_[/COLOR] my problem of receiving files from my android phone.

---

### Post by leonbravo on 2012-02-26
> **seapaladin said:**
> Ubuntu 11.10 all updates done (including pre-released-updates)  , personal file sharing activated ( it complain about missing packages an y found the solution on google , install apache2.2-bin and libapache2-mod-dnssd  ) and still "browse files" function not functional from nautilus . From terminal it works for me using this commands 
"obexfs -b PUT-HERE-YOUR-DEVICE-ADDRES ~/nokia " (to mount my e90 )
"fusermount --u ~/nokia" (unmount my device )
hope this help someone

works here!!.

---

### Post by 3dmatrix on 2012-03-17
"obexfs -b PUT-HERE-YOUR-DEVICE-ADDRES ~/nokia " (to mount my e90 )
"fusermount --u ~/nokia" (unmount my device )

The above command works but speed is terribly slow.
Can rarely transfer files.
Any better solution ?

---

### Post by khurtsiya on 2012-03-18
> **Jordanbadangayon said:**
> Try opening 'personal file sharing' from dash...

Someone please help me find this in Ubuntu 11.10

---

### Post by CaptainMark on 2012-03-18
apparently the latest kernel thats been put into precise fixes the transfer issue, not the browsing issue fullly yet, my phones away for repairs atm so i cant test this yet any takers?

---

### Post by apoapo on 2012-03-18
Sending and receiving single files works here, browsing doesn't.

Lets hope they get this done till 12.04 :/

---

### Post by romankarlfranz on 2012-05-05
Dbus error also in Linux Mint 12.

any solution yet.

i could send a file to my Samsung phone
no browsing

---

### Post by sehari24jam on 2012-06-21
I have similar problem with Ubuntu 12.04 (Toshiba laptop/integrated-bluetooth vs Nokia C7).
Condition:
1. I can send file from laptop to phone (got some warning at phone, but it works).
2. I can not send file from phone to laptop (no matter what I do).
3. "Browse files" from bluetooth laptop service works.

Somehow I got (solving point 2):
a. From laptop, "Browse files" of the phone.
b. Then suddenly you can send file from Phone to Laptop.

---

### Post by 3dmatrix on 2012-06-23
Till Ubuntu 10.04 I never had any such problem but since i shifted to 11.10 i face a lot of problem with bluetooth.

Why does Ubuntu downgrades itself while upgrading :)

---

### Post by Slevin87 on 2012-07-23
Hi,
I have the same problem in Ubuntu12.10 (and also with openSUSE11.4 & 12.1).
Is it really a dbus error? What's exactly the problem there? In which version of dbus appears this error?
Does anyone have a working solution for it? Or is the only possibility to downgrade to Ubuntu11.04 ?

---

### Post by w o l f on 2012-11-11
I have the same problem after I upgraded to 12.04, everything seems to works properly in 11.10.

---

### Post by gepatino on 2013-01-08
I know this thread is a bit old, but did anyone solved the bluetooth issues in 12.04? 

I'm stuck to that version because of corporate policies and can't make my phone work as a dial up network. (it used to work as a charm in some previous ubuntu version).


Thanks a lot

---

### Post by espmartin on 2013-03-10
> **gepatino said:**
> I know this thread is a bit old, but did anyone solved the bluetooth issues in 12.04? 

I'm stuck to that version because of corporate policies and can't make my phone work as a dial up network. (it used to work as a charm in some previous ubuntu version).


Thanks a lot

It's March 10th, 2013 - and same problem issue here on Ubuntu 12.10...

---

### Post by CaptainMark on 2013-03-11
You can send files to a device but can't receive them onto your pc.  I feel this is something that will be stuck with us for too long, since I reported this bug on launchpad nearly 18 months ago [https://bugs.launchpad.net/gnome-bluetooth/+bug/872044](https://bugs.launchpad.net/gnome-bluetooth/+bug/872044), several discussions, several patches and several hundred participants later and this bug is still not fixed.

---

