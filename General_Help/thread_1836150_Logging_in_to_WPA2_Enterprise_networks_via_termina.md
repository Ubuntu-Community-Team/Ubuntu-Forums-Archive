---
title: "Logging in to WPA2 Enterprise networks via terminal"
date: 2011-08-30
forum: General Help
---

### Post by Anonymous Citizen on 2011-08-30
I don't need this as I can do this via the GUI, but I was just wondering about the procedure for logging into WPA2 Enterprise networks via the terminal. I have read up a bit on wpa_supplicant, wpa_suplicant.conf, and wpa_passphrase. I would like to be able to do this on my school network. Here is the scan:

```
Cell 23 - Address: [MAC Address]
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"SchoolWPA"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000069509d2abc
                    Extra: Last beacon: 1780ms ago
                    IE: Unknown: 000975697774782D777061
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 0B0500001F8D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E05008F000F00FF0359004C6962313134322D343400000000000000000036
                    IE: Unknown: 9606004096000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
```Now, the school uses a login and password for the network. That's it. I don't seem to need a certificate, although there is this Java applet on my Mac that I looked at the code for that had some certificate. You can login just through the normal wireless settings and choose WPA2 Enterprise and put in your login information, but the Java application you can download when you try to connect. I ran that first on my Mac before I just logged in normally, so I'm assuming I have the cert saved or something? I'm trying to learn more about WPA2 and so forth by doing this through the command line. I did go by the IT department. They said that all I may have to do is log in with my school user name and password because the same Java app for Windows and Mac can't be downloaded for Linux. I didn't expect them to tell me how to use the terminal to access the network. 

Sorry for any noob questions on my part. As I said, I'm trying to learn.

---

### Post by Anonymous Citizen on 2011-08-30
It seems I can log in with LEAP via Network Manager just fine. I didn't even try until today. As I said, I would like to learn how to use the terminal only though.

---

### Post by bodhi.zazen on 2011-08-30
You use wpa supplicant

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

