---
title: "How to configure Huawei E220"
date: 2009-08-24
forum: General Help
---

### Post by ExtremeCoolSha on 2009-08-24
I want to configure the Huawei E220 modem I recently bought in Fedora 10. I read lot of detail documents in the internet. All were interesting and explaining the wvdial.conf file. The problem I have is that, the file asks for the phone # to dial, username & a password. I don't have these information since my ISP didn't provide those.
It works perfectly in Windows, in which above information are not needed, because when plugged in Windows, a software installation launches, which does the job to connect to the internet.
So, is there a way to configure the modem to connect to the internet without those information. Because my ISP refuses to provide those, when I called there customer services.

---

### Post by P4man on 2009-08-24
the network manager in gnome fills out that info automatically for a huge list of providers. Tell me your country and provider, and Ill tell you what it gives me.

---

### Post by ExtremeCoolSha on 2009-08-24
My Country is: Sri Lanka

Provider : Dialog Telekom

---

### Post by P4man on 2009-08-24
Dialog postpaid:

number: *99#
username and password: blank
APN: [www.dialogsl.com](www.dialogsl.com)


Dialog prepaid:

number: *99#
username and password: blank
APN: ppinternet

---

### Post by GeorgeVita on 2009-08-25
Hi **P4man**, I am coming here as the subject is the same with: [http://ubuntuforums.org/showthread.php?t=1247928](http://ubuntuforums.org/showthread.php?t=1247928)

----------

Hi, **ExtremeCoolSha**, searching ubuntuforums for 'Dialog GSM Huawei E220' found your [2nd thread]("http://ubuntuforums.org/showthread.php?t=1248538") about the same subject.

I am seen the same data from network manager settings (if are updated, I cannot test) as: > **P4man said:**
> the network manager in gnome fills out that info automatically for a huge list of providers. Tell me your country and provider, and Ill tell you what it gives me. > **P4man said:**
> Dialog postpaid:
number: *99#
username and password: blank
APN: [www.dialogsl.com](www.dialogsl.com)

Dialog prepaid:
number: *99#
username and password: blank
APN: ppinternet
So you do not need to try #777
Just check that Ubintu version is 9.04 (which has an updated network manager), add this connection, check that setting are as above and of course:
First check that your modem is connected and found by your system:
- boot without modem, **wait** for the system to load, attach modem, **wait** 10 seconds, try ```
dmesg | grep ttyU
``` to see any port created.

Regards,
George

---

### Post by ExtremeCoolSha on 2009-08-25
Thanks for your replies guys!

Sorry to make you see the thread in 2 places. I thought my first post was missing & I started another one. Eventually I found GoergeVita has replied for my 1st post.
Anyway my device is recognized by Ubuntu when I plugged it. As soon as I plugged it I could see a message at the top right that the Huawei modem is connected. It asked to click that icon to make the configuration. In that I entered the details as above. Soon after the details were applied, the place displayed the message, " Click here to connect ", so I clicked and selected the , modem. Unfortunately nothing happens. I still couldn't connect. Seems to be a different issue. Any Ideas guys?

---

### Post by ExtremeCoolSha on 2009-08-25
Thanks guys!

Sorry to trouble you in two places. My modem is detected by Ubuntu. As soon as I plugged it a message appeared at the to right saying New device "Huawei Modem" found & click to configure. I clicked and followed the instructions with above details(phone #, APN). After finishing the same place asked me to click to connect. I clicked and selected my modem. Nothing seems to be happening. The connection is not formed yet. Any ideas guys?

---

### Post by GeorgeVita on 2009-08-25
Hi **ExtremeCoolSha**, provide some more info:

Ubuntu version (and if it is updated using other internet connection))
Network Manager version (right click icon, About)
kernel version, from terminal: **uname -a**
While 'trying to connect' does it shows any message?

Also try to connect with ethernet disconnected and WiFi (if any) disabled.

G

---

### Post by ExtremeCoolSha on 2009-08-25
The Ubuntu version I'm using is 8.10 not the new 9.04. The Network Manager version is 0.7.0. After I click the mobile broadband connection it say "connection not established". 
Can u pls explain how to diable Wifi & ethernet.And also say me, should I keep the user name & password fields blank or type the word 'blank'.

---

### Post by GeorgeVita on 2009-08-25
Sorry for 'moving' you to terminal but as you have 8.10 please try another method:
```
gksudo gedit /etc/wvdial.conf
```Copy/paste into that file the lines below (delete any other existing): ```

[Dialer Defaults]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99#
Stupid Mode = 1
Dial Attempts = 1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","www.dialogsl.com"

[Dialer prepaid]
Init3 =AT+CGDCONT=1,"IP","ppinternet"

```SAVE, Close gedit, try to connect with:
```
sudo wvdial
```
or for **prepaid** account: ```
sudo wvdial prepaid
```

If connected, open Firefox and reemove Offline Mode with **ALT-F W**
Disconnects with CTRL-C at the terminal window you made (hope) the connection.

Regards,
George

Post here all results.

---

### Post by P4man on 2009-08-25
just to point out, when I wrote blank, I meant empty, nothing, nill, nada.. not b-l-a-n-k :)

not sure if GeorgeVita's config file needs changing to accommodate this or not.

---

### Post by GeorgeVita on 2009-08-25
Hi **P4man**,
at wvdial.conf you cannot use null user/password fields (creates an error) so my scope is to have at least an error message to understand (I have more experience with wvdial than with N.M.07). E220 is the 'standard', it should work.

Another idea is to 'dig' inside windows modem log files and extract some init strings but I cannot remember the terminology of windows to help **ExtremeCoolSha** find them.

Also many things have changed from 8.10 to 9.04 regarding N.M and 3G

(OffTopic: I shame to express an idea at 'Brainstorming forum' for a "windows desktop simulator" within Ubuntu!)

Regards,
George

---

