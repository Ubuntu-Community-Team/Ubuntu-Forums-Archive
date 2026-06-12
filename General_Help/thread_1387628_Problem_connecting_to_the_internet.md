---
title: "Problem connecting to the internet"
date: 2010-01-22
forum: General Help
---

### Post by cnf17 on 2010-01-22
Hope this is not a tired old rehash but.....I have two computers here. A Sony running Windows 7 and a Toshiba running Vista 64. Both connect O.K. via wireless. I have loaded Ubuntu onto both machines to run with the MS products. The Sony connects but the Toshiba does not and I don't seem to be getting anywhere with this problem. I would appreciate some ideas and suggestions in a way that a computer deadhead like myself can follow......Thanks

---

### Post by Saiko Berry on 2010-01-22
apt-get install wicd
nohup wicd-client &

try that. setup wireless etc.

---

### Post by clhsharky on 2010-01-22
HI

Info on harware please,
good place to start.

Networking & Wireless
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Sharky

---

### Post by cnf17 on 2010-01-22
Hi Sharky,
The Sony is a VGN-CR35G laptop and the Toshiba, a P505. The router is a Netcomm NB6Plus4W. I updated the driver on the Toshiba. As I said with the two versions of Windows the computers connect automatically and the Sony connects automatically when using Ubuntu. The Toshiba has a strong signal and good connectivity in Windows but shows no signal and also gives no wireless options in Ubuntu. I hope that gives you some clue....All the best.

---

### Post by cnf17 on 2010-01-23
hi Saiko Berry,
tried that I asume in terminaal. No Luck. Ive tried filling in the SSID and Bssid etc and password. Still nothing. I cannot understand why my other laptop connects without a problem. I have read other threads where a lot of people seem to have a variation on this problem.
Thanks for the help so far.

---

### Post by Jackzor on 2010-01-23
This may sound dumb.. But.. Just in case right click the network icon in your tray and make sure wireless is enabled :(

For some reason when I installed on my laptop is was not checked.

---

### Post by Iowan on 2010-01-23
**sudo lshw -C network** will provide valuable information on your network devices.

---

### Post by cnf17 on 2010-01-23
Hi Jackzor,
I have tried the right click on the network icon and here is the next problem. Sometimes the drop down box has 'enable wireless' but it is greyed out. Most of the time however the 'enable' option is not present. The same is the case with a right click. Sometimes 'wired network' is present and sometimes not. Looking through other threads in other sections I have the idea that I am not the first to have encountered this quirk but as yet I have not seen a simply stated solution. Please, any suggestions in 'Ubunto for dummies' form. Thanks in advance for the expected torrent of replies.

---

### Post by cnf17 on 2010-01-23
Sorry, should have been 'left click' when refering to 'wired network' See above.

---

