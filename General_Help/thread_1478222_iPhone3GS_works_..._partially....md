---
title: "iPhone3GS works ... partially..."
date: 2010-05-09
forum: General Help
---

### Post by eltonw on 2010-05-09
_IF THIS HELPS_ ANYONE:

Since installing **LUCID LYNX LTS** on my NETBOOK
(SEE: [http://ubuntuforums.org/showthread.php?p=9203922#post9203922]("http://ubuntuforums.org/showthread.php?p=9203922#post9203922")  [#136] )

***[COLOR="Sienna"][SIZE="2"]Via USB[/SIZE][/COLOR]***, I  can connect my **iPhone 3GS**. It gives me two simultaneous choices:
Open F-Spot and Open Rythmbox.
In addition, I can also "Open / Browse Folder"
As such, I can view / import photos and videos made on the phone, as well as video PODCASTS
I can also play my music files 

[COLOR="Red"]WHAT I **cannot** DO:[/COLOR]
1) play / find my purchased audiobooks [[COLOR="Blue"]decryption not supported[/COLOR]]
2) locate the mp4 videos / movies (_*NOT encrypted*_) that I transferred to the phone via iTunes on my MacBook.
3) send a file **[COLOR="Blue"][SIZE="2"]via bluetooth[/SIZE][/COLOR]** to the phone [the Indicator Applet does allow me go go as far as select the file. It gets to the point of "connecting" then "unknown error occurred"

[FONT="Trebuchet MS"][COLOR="Olive"]I cannot sync the addressbook, calendar, or notes on the iPhone with my netbook.
(Perhaps someone would kindly point me in the right direction?)[/COLOR][/FONT]


I have the following libraries installed:

ifuse
libmobiledevice-utils
libmobiledevice0
libplist++1
libplist1
libusbmuxd1
python-imobildevice
usbmuxd

NOTA BENE: This phone is NOT jail-broken.

If anyone can add / improve / update this, it would be most appreciated!

respectfully,

---

### Post by Apuokas on 2010-05-31
Hi there, eltonw,

What FW version do you use on your iPhone? I have a Lucid Lynx Netbook Edition on my Asus EEE 1000H and can't access my iPhone.

I was thinking, might it be because of the Netbook Edition? I was also trying to get to iPhone via live CD version of Lucid Lynx Desktop Edition, but with no luck.

Any suggestions?

PS. When I connect iPhone via USB cable, just nothing happens

---

### Post by eltonw on 2010-05-31
> **Apuokas said:**
> Hi there, eltonw,

What FW version do you use on your iPhone? I have a Lucid Lynx Netbook Edition on my Asus EEE 1000H and can't access my iPhone.

I was thinking, might it be because of the Netbook Edition? I was also trying to get to iPhone via live CD version of Lucid Lynx Desktop Edition, but with no luck.

Any suggestions?

PS. When I connect iPhone via USB cable, just nothing happens

[COLOR="Red"][FONT="Trebuchet MS"]Have you installed any of the libs mentioned in my posting?[/FONT][/COLOR]

Perhaps I was not sufficiently clear:

I looked in **Synaptic**, and did a **search** in the *descriptions* for "iPhone". 
After looking at the results, I *[COLOR="DarkRed"]installed the following libraries[/COLOR]* ([COLOR="DarkRed"]per my posting above[/COLOR]):

ifuse
libmobiledevice-utils
libmobiledevice0
libplist++1
libplist1
libusbmuxd1
python-imobildevice
usbmuxd

I can connect my EEE 1000 PC and the iPhone via USB to navigate it as an attached device. For file read/write the iPhone will ONLY function via USB, [COLOR="DarkRed"]*provided that*[/COLOR] the aforementioned libraries are installed. 
[SIZE="3"]The firmware version / OS version on my iPhone 3GS is 3.1.3.[/SIZE]
Even on my MacBook with Snow Leopard (OSX 10.6.3), I am obliged to connect via USB to sync the phone.#-o 
It is NOT jailbroken (...yet)

[FONT="Trebuchet MS"]WRT [COLOR="Blue"]Bluetooth[/COLOR], the iPhone acts like a tethered wifi device, one cannot transfer files nor navigate it via blutooth.[/FONT]

**/REM**: Previously with GAMMU / WAMMU, I used to sync my addressbook and calendar, using a *SONY ERICSSON* phone. Perhaps I might try and see if GAMMU might work with the Apple product.

[COLOR="DarkOrange"][FONT="Comic Sans MS"][SIZE="2"]The version of LUCID LYNX that I have installed is the Netbook Remix[/SIZE][/FONT][/COLOR].

---

