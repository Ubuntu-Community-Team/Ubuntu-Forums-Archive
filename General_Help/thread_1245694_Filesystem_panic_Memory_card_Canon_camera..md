---
title: "Filesystem panic: Memory card Canon camera."
date: 2009-08-20
forum: General Help
---

### Post by benne on 2009-08-20
Good evening ladies and gentlemen. I present to you one problem. 

I shot 1.7G of photographs on my holiday, all went on same CF memory card ad wasnt attached to a computer the whole time. 

I plug the card into my usb card reader and the cards filesystem pops nicely up in Gnome but with the title "JO NAMA" and (appears) with no contents. 

df -h reveals that it is reporting the right avalible space. 

```
$ df -h | grep NAMA
/dev/sdd1             2.0G  1.7G  272M  87% /media/JO NAMA

```

dmesg shows me this error repeated times:
```
[35418.302700] FAT: Filesystem panic (dev sdd1)
[35418.302709]     invalid access to FAT (entry 0x0000fbff)
[35418.302700] FAT: Filesystem panic (dev sdd1)
[35417.431867]     invalid access to FAT (entry 0x0000fbff)
[35418.302700] FAT: Filesystem panic (dev sdd1)
[35417.431867]     invalid access to FAT (entry 0x0000fbff)

```

and fsck.msdos reports "Too many errors to continue" after several illegal filenames fixed. 

So I figure that since my camera managed to read the card, then it must work if i simply plug the camera to the computer. 

This does not work, I find the following errors:

Gnome
```
Sorry, could not display all the contents of "Canon, Inc. EOS 20D": Failed to get folder list: -111: Invalid filename
```

dmesg (i feel like there is something missing):
```

[CODE][35658.751339] usb 1-6.2: USB disconnect, address 28
[35664.840839] usb 1-6.2: new high speed USB device using ehci_hcd and address 29
[35664.956925] usb 1-6.2: configuration #1 chosen from 1 choice


```

To be sure not to wreck the card totally i use dd to make a image of it. Run fsck.msos 3 times and the same error comes again and again. I tried PhotoRec with no luck. I opened a windows virtual machine, tried r-studio  as somebody suggested to me. With no luck. But it kept saying: "Invalid cluster: **0xfbff**, file was shrunk".

FBFF is the same hex that was in the demsg when it reported File system panic. But this isn't a complete HEX, 2 characters missing. I'm utterly confused.

---

### Post by benne on 2009-08-20
I should note that I have only tried one card reader. But i have tried two CF cards and its only this one behaving like that. I have yet to try another reader though, and another camera.

And i just discovered this by running fsck.msdos without the -a switch

```
Cluster 0 out of range (64511 > 62471). Setting to EOF.
Cluster 1 out of range (64511 > 62471). Setting to EOF.
Cluster 151 out of range (64511 > 62471). Setting to EOF.
Cluster 297 out of range (64511 > 62471). Setting to EOF.
Cluster 443 out of range (64511 > 62471). Setting to EOF.
Cluster 589 out of range (64511 > 62471). Setting to EOF.
Cluster 734 out of range (64511 > 62471). Setting to EOF.
Cluster 884 out of range (64511 > 62471). Setting to EOF.
Cluster 1030 out of range (64511 > 62471). Setting to EOF.
Cluster 1177 out of range (64511 > 62471). Setting to EOF.
Cluster 1248 out of range (64511 > 62471). Setting to EOF.
Cluster 1325 out of range (64511 > 62471). Setting to EOF.
Cluster 1380 out of range (64511 > 62471). Setting to EOF.
Cluster 1437 out of range (64511 > 62471). Setting to EOF.
Cluster 1509 out of range (64511 > 62471). Setting to EOF.
Cluster 1576 out of range (64511 > 62471). Setting to EOF.
Cluster 1658 out of range (64511 > 62471). Setting to EOF.
Cluster 1745 out of range (64511 > 62471). Setting to EOF.
Cluster 1827 out of range (64511 > 62471). Setting to EOF.
Cluster 1910 out of range (64511 > 62471). Setting to EOF.
Cluster 1999 out of range (64511 > 62471). Setting to EOF.
Cluster 2085 out of range (64511 > 62471). Setting to EOF.
Cluster 2178 out of range (64511 > 62471). Setting to EOF.
Cluster 2327 out of range (64511 > 62471). Setting to EOF.
Cluster 2419 out of range (64511 > 62471). Setting to EOF.
Cluster 2510 out of range (64511 > 62471). Setting to EOF.
Cluster 2595 out of range (64511 > 62471). Setting to EOF.
Cluster 2677 out of range (64511 > 62471). Setting to EOF.
Cluster 2755 out of range (64511 > 62471). Setting to EOF.
Cluster 2834 out of range (64511 > 62471). Setting to EOF.
Cluster 2913 out of range (64511 > 62471). Setting to EOF.
Cluster 3053 out of range (64511 > 62471). Setting to EOF.
Cluster 3158 out of range (64511 > 62471). Setting to EOF.
Cluster 3272 out of range (64511 > 62471). Setting to EOF.
Cluster 3389 out of range (64511 > 62471). Setting to EOF.
Cluster 3513 out of range (64511 > 62471). Setting to EOF.
Cluster 3619 out of range (64511 > 62471). Setting to EOF.
Cluster 3722 out of range (64511 > 62471). Setting to EOF.
Cluster 3836 out of range (64511 > 62471). Setting to EOF.
Cluster 3961 out of range (64511 > 62471). Setting to EOF.
Cluster 3962 out of range (64511 > 62471). Setting to EOF.
Cluster 4094 out of range (64511 > 62471). Setting to EOF.
Cluster 4163 out of range (64511 > 62471). Setting to EOF.
Cluster 4244 out of range (64511 > 62471). Setting to EOF.
Cluster 4330 out of range (64511 > 62471). Setting to EOF.
Cluster 4404 out of range (64511 > 62471). Setting to EOF.
Cluster 4482 out of range (64511 > 62471). Setting to EOF.
Cluster 4562 out of range (64511 > 62471). Setting to EOF.
Cluster 4715 out of range (64511 > 62471). Setting to EOF.
Cluster 4716 out of range (64511 > 62471). Setting to EOF.
Cluster 4780 out of range (64511 > 62471). Setting to EOF.
Cluster 4872 out of range (64511 > 62471). Setting to EOF.
Cluster 4964 out of range (64511 > 62471). Setting to EOF.
Cluster 5066 out of range (64511 > 62471). Setting to EOF.
Cluster 5166 out of range (64511 > 62471). Setting to EOF.
Cluster 5230 out of range (64511 > 62471). Setting to EOF.
Cluster 5295 out of range (64511 > 62471). Setting to EOF.
Cluster 5383 out of range (64511 > 62471). Setting to EOF.
Cluster 5461 out of range (64511 > 62471). Setting to EOF.
Cluster 5589 out of range (64511 > 62471). Setting to EOF.
Cluster 5715 out of range (64511 > 62471). Setting to EOF.
Cluster 5828 out of range (64511 > 62471). Setting to EOF.
Cluster 5986 out of range (64511 > 62471). Setting to EOF.
Cluster 6144 out of range (64511 > 62471). Setting to EOF.
Cluster 6215 out of range (64511 > 62471). Setting to EOF.
Cluster 6309 out of range (64511 > 62471). Setting to EOF.
Cluster 6399 out of range (64511 > 62471). Setting to EOF.
Cluster 6490 out of range (64511 > 62471). Setting to EOF.
Cluster 6582 out of range (64511 > 62471). Setting to EOF.
Cluster 6676 out of range (64511 > 62471). Setting to EOF.
Cluster 6766 out of range (64511 > 62471). Setting to EOF.
Cluster 6865 out of range (64511 > 62471). Setting to EOF.
Cluster 6959 out of range (64511 > 62471). Setting to EOF.
Cluster 7056 out of range (64511 > 62471). Setting to EOF.
Cluster 7148 out of range (64511 > 62471). Setting to EOF.
Cluster 7253 out of range (64511 > 62471). Setting to EOF.
Cluster 7352 out of range (64511 > 62471). Setting to EOF.
Cluster 7451 out of range (64511 > 62471). Setting to EOF.
Cluster 7551 out of range (64511 > 62471). Setting to EOF.
Cluster 7638 out of range (64511 > 62471). Setting to EOF.
Cluster 7723 out of range (64511 > 62471). Setting to EOF.
Cluster 7789 out of range (64511 > 62471). Setting to EOF.
Cluster 7863 out of range (64511 > 62471). Setting to EOF.
Cluster 7937 out of range (64511 > 62471). Setting to EOF.
Cluster 8015 out of range (64511 > 62471). Setting to EOF.
Cluster 8089 out of range (64511 > 62471). Setting to EOF.
Cluster 8167 out of range (64511 > 62471). Setting to EOF.
Cluster 8241 out of range (64511 > 62471). Setting to EOF.
Cluster 8330 out of range (64511 > 62471). Setting to EOF.
Cluster 8420 out of range (64511 > 62471). Setting to EOF.
Cluster 8511 out of range (64511 > 62471). Setting to EOF.
Cluster 8599 out of range (64511 > 62471). Setting to EOF.
Cluster 8688 out of range (64511 > 62471). Setting to EOF.
Cluster 8782 out of range (64511 > 62471). Setting to EOF.
Cluster 8868 out of range (64511 > 62471). Setting to EOF.
Cluster 8956 out of range (64511 > 62471). Setting to EOF.
Cluster 9054 out of range (64511 > 62471). Setting to EOF.
Cluster 9156 out of range (64511 > 62471). Setting to EOF.
Cluster 9255 out of range (64511 > 62471). Setting to EOF.
Cluster 9354 out of range (64511 > 62471). Setting to EOF.
Cluster 9451 out of range (64511 > 62471). Setting to EOF.
Cluster 9553 out of range (64511 > 62471). Setting to EOF.
Cluster 9652 out of range (64511 > 62471). Setting to EOF.
Cluster 9748 out of range (64511 > 62471). Setting to EOF.
Cluster 9834 out of range (64511 > 62471). Setting to EOF.
Cluster 9920 out of range (64511 > 62471). Setting to EOF.
Cluster 10005 out of range (64511 > 62471). Setting to EOF.
Cluster 10103 out of range (64511 > 62471). Setting to EOF.
Cluster 10189 out of range (64511 > 62471). Setting to EOF.
Cluster 10277 out of range (64511 > 62471). Setting to EOF.
Cluster 10350 out of range (64511 > 62471). Setting to EOF.
Cluster 10445 out of range (64511 > 62471). Setting to EOF.
Cluster 10536 out of range (64511 > 62471). Setting to EOF.
Cluster 10635 out of range (64511 > 62471). Setting to EOF.
Cluster 10741 out of range (64511 > 62471). Setting to EOF.
Cluster 10840 out of range (64511 > 62471). Setting to EOF.
Cluster 10938 out of range (64511 > 62471). Setting to EOF.
Cluster 11098 out of range (64511 > 62471). Setting to EOF.
Cluster 11226 out of range (64511 > 62471). Setting to EOF.
Cluster 11358 out of range (64511 > 62471). Setting to EOF.
Cluster 11492 out of range (64511 > 62471). Setting to EOF.
Cluster 11629 out of range (64511 > 62471). Setting to EOF.
Cluster 11764 out of range (64511 > 62471). Setting to EOF.
Cluster 11873 out of range (64511 > 62471). Setting to EOF.
Cluster 11991 out of range (64511 > 62471). Setting to EOF.
Cluster 12101 out of range (64511 > 62471). Setting to EOF.
Cluster 12209 out of range (64511 > 62471). Setting to EOF.
Cluster 12316 out of range (64511 > 62471). Setting to EOF.
Cluster 12420 out of range (64511 > 62471). Setting to EOF.
Cluster 12522 out of range (64511 > 62471). Setting to EOF.
Cluster 12624 out of range (64511 > 62471). Setting to EOF.
Cluster 12735 out of range (64511 > 62471). Setting to EOF.
Cluster 12827 out of range (64511 > 62471). Setting to EOF.
Cluster 12925 out of range (64511 > 62471). Setting to EOF.
Cluster 13027 out of range (64511 > 62471). Setting to EOF.
Cluster 13143 out of range (64511 > 62471). Setting to EOF.
Cluster 13230 out of range (64511 > 62471). Setting to EOF.
Cluster 13324 out of range (64511 > 62471). Setting to EOF.
Cluster 13436 out of range (64511 > 62471). Setting to EOF.
Cluster 13543 out of range (64511 > 62471). Setting to EOF.
Cluster 13644 out of range (64511 > 62471). Setting to EOF.
Cluster 13750 out of range (64511 > 62471). Setting to EOF.
Cluster 13837 out of range (64511 > 62471). Setting to EOF.
Cluster 13938 out of range (64511 > 62471). Setting to EOF.
Cluster 14029 out of range (64511 > 62471). Setting to EOF.
Cluster 14030 out of range (64511 > 62471). Setting to EOF.
Cluster 14122 out of range (64511 > 62471). Setting to EOF.
Cluster 14218 out of range (64511 > 62471). Setting to EOF.
Cluster 14354 out of range (64511 > 62471). Setting to EOF.
Cluster 14449 out of range (64511 > 62471). Setting to EOF.
Cluster 14537 out of range (64511 > 62471). Setting to EOF.
Cluster 14632 out of range (64511 > 62471). Setting to EOF.
Cluster 14731 out of range (64511 > 62471). Setting to EOF.
Cluster 14837 out of range (64511 > 62471). Setting to EOF.
Cluster 14922 out of range (64511 > 62471). Setting to EOF.
Cluster 15006 out of range (64511 > 62471). Setting to EOF.
Cluster 15073 out of range (64511 > 62471). Setting to EOF.
Cluster 15152 out of range (64511 > 62471). Setting to EOF.
Cluster 15235 out of range (64511 > 62471). Setting to EOF.
Cluster 15328 out of range (64511 > 62471). Setting to EOF.
Cluster 15421 out of range (64511 > 62471). Setting to EOF.
Cluster 15510 out of range (64511 > 62471). Setting to EOF.
Cluster 15593 out of range (64511 > 62471). Setting to EOF.
Cluster 15681 out of range (64511 > 62471). Setting to EOF.
Cluster 15780 out of range (64511 > 62471). Setting to EOF.
Cluster 15881 out of range (64511 > 62471). Setting to EOF.
Cluster 15988 out of range (64511 > 62471). Setting to EOF.
Cluster 16077 out of range (64511 > 62471). Setting to EOF.
Cluster 16183 out of range (64511 > 62471). Setting to EOF.
Cluster 16332 out of range (64511 > 62471). Setting to EOF.
Cluster 16481 out of range (64511 > 62471). Setting to EOF.
Cluster 16595 out of range (64511 > 62471). Setting to EOF.
Cluster 16748 out of range (64511 > 62471). Setting to EOF.
Cluster 16858 out of range (64511 > 62471). Setting to EOF.
Cluster 17002 out of range (64511 > 62471). Setting to EOF.
Cluster 17087 out of range (64511 > 62471). Setting to EOF.
Cluster 17216 out of range (64511 > 62471). Setting to EOF.
Cluster 17345 out of range (64511 > 62471). Setting to EOF.
Cluster 17486 out of range (64511 > 62471). Setting to EOF.
Cluster 17627 out of range (64511 > 62471). Setting to EOF.
Cluster 17767 out of range (64511 > 62471). Setting to EOF.
Cluster 17899 out of range (64511 > 62471). Setting to EOF.
Cluster 18036 out of range (64511 > 62471). Setting to EOF.
Cluster 18171 out of range (64511 > 62471). Setting to EOF.
Cluster 18307 out of range (64511 > 62471). Setting to EOF.
Cluster 18443 out of range (64511 > 62471). Setting to EOF.
Cluster 18581 out of range (64511 > 62471). Setting to EOF.
Cluster 18718 out of range (64511 > 62471). Setting to EOF.
Cluster 18856 out of range (64511 > 62471). Setting to EOF.
Cluster 18996 out of range (64511 > 62471). Setting to EOF.
Cluster 19135 out of range (64511 > 62471). Setting to EOF.
Cluster 19276 out of range (64511 > 62471). Setting to EOF.
Cluster 19417 out of range (64511 > 62471). Setting to EOF.
Cluster 19554 out of range (64511 > 62471). Setting to EOF.
Cluster 19692 out of range (64511 > 62471). Setting to EOF.
Cluster 19830 out of range (64511 > 62471). Setting to EOF.
Cluster 19960 out of range (64511 > 62471). Setting to EOF.
Cluster 20085 out of range (64511 > 62471). Setting to EOF.
Cluster 20210 out of range (64511 > 62471). Setting to EOF.
Cluster 20335 out of range (64511 > 62471). Setting to EOF.
Cluster 20469 out of range (64511 > 62471). Setting to EOF.
Cluster 20609 out of range (64511 > 62471). Setting to EOF.
Cluster 20745 out of range (64511 > 62471). Setting to EOF.
Cluster 20880 out of range (64511 > 62471). Setting to EOF.
Cluster 21016 out of range (64511 > 62471). Setting to EOF.
Cluster 21153 out of range (64511 > 62471). Setting to EOF.
Cluster 21291 out of range (64511 > 62471). Setting to EOF.
Cluster 21422 out of range (64511 > 62471). Setting to EOF.
Cluster 21553 out of range (64511 > 62471). Setting to EOF.
Cluster 21678 out of range (64511 > 62471). Setting to EOF.
Cluster 21805 out of range (64511 > 62471). Setting to EOF.
Cluster 21928 out of range (64511 > 62471). Setting to EOF.
Cluster 22052 out of range (64511 > 62471). Setting to EOF.
Cluster 22183 out of range (64511 > 62471). Setting to EOF.
Cluster 22314 out of range (64511 > 62471). Setting to EOF.
Cluster 22446 out of range (64511 > 62471). Setting to EOF.
Cluster 22578 out of range (64511 > 62471). Setting to EOF.
Cluster 22725 out of range (64511 > 62471). Setting to EOF.
Cluster 22872 out of range (64511 > 62471). Setting to EOF.
Cluster 23020 out of range (64511 > 62471). Setting to EOF.
Cluster 23154 out of range (64511 > 62471). Setting to EOF.
Cluster 23286 out of range (64511 > 62471). Setting to EOF.
Cluster 23417 out of range (64511 > 62471). Setting to EOF.
Cluster 23549 out of range (64511 > 62471). Setting to EOF.
Cluster 23680 out of range (64511 > 62471). Setting to EOF.
Cluster 23813 out of range (64511 > 62471). Setting to EOF.
Cluster 23948 out of range (64511 > 62471). Setting to EOF.
Cluster 24084 out of range (64511 > 62471). Setting to EOF.
Cluster 24220 out of range (64511 > 62471). Setting to EOF.
Cluster 24354 out of range (64511 > 62471). Setting to EOF.
Cluster 24488 out of range (64511 > 62471). Setting to EOF.
Cluster 24623 out of range (64511 > 62471). Setting to EOF.
Cluster 24758 out of range (64511 > 62471). Setting to EOF.
Cluster 24892 out of range (64511 > 62471). Setting to EOF.
Cluster 25037 out of range (64511 > 62471). Setting to EOF.
Cluster 25181 out of range (64511 > 62471). Setting to EOF.
Cluster 25326 out of range (64511 > 62471). Setting to EOF.
Cluster 25472 out of range (64511 > 62471). Setting to EOF.
Cluster 25618 out of range (64511 > 62471). Setting to EOF.
Cluster 25764 out of range (64511 > 62471). Setting to EOF.
Cluster 25910 out of range (64511 > 62471). Setting to EOF.
Cluster 26055 out of range (64511 > 62471). Setting to EOF.
Cluster 26199 out of range (64511 > 62471). Setting to EOF.
Cluster 26327 out of range (64511 > 62471). Setting to EOF.
Cluster 26458 out of range (64511 > 62471). Setting to EOF.
Cluster 26588 out of range (64511 > 62471). Setting to EOF.
Cluster 26589 out of range (64511 > 62471). Setting to EOF.
Cluster 26719 out of range (64511 > 62471). Setting to EOF.
Cluster 26849 out of range (64511 > 62471). Setting to EOF.
Cluster 26996 out of range (64511 > 62471). Setting to EOF.
Cluster 27143 out of range (64511 > 62471). Setting to EOF.
Cluster 27289 out of range (64511 > 62471). Setting to EOF.
Cluster 27438 out of range (64511 > 62471). Setting to EOF.
Cluster 27586 out of range (64511 > 62471). Setting to EOF.
Cluster 27734 out of range (64511 > 62471). Setting to EOF.
Cluster 27876 out of range (64511 > 62471). Setting to EOF.
Cluster 28020 out of range (64511 > 62471). Setting to EOF.
Cluster 28167 out of range (64511 > 62471). Setting to EOF.
Cluster 28315 out of range (64511 > 62471). Setting to EOF.
Cluster 28461 out of range (64511 > 62471). Setting to EOF.
Cluster 28607 out of range (64511 > 62471). Setting to EOF.
Cluster 28752 out of range (64511 > 62471). Setting to EOF.
Cluster 28898 out of range (64511 > 62471). Setting to EOF.
Cluster 29046 out of range (64511 > 62471). Setting to EOF.
Cluster 29193 out of range (64511 > 62471). Setting to EOF.
Cluster 29341 out of range (64511 > 62471). Setting to EOF.
Cluster 29475 out of range (64511 > 62471). Setting to EOF.
Cluster 29606 out of range (64511 > 62471). Setting to EOF.
Cluster 29735 out of range (64511 > 62471). Setting to EOF.
Cluster 29861 out of range (64511 > 62471). Setting to EOF.
Cluster 30007 out of range (64511 > 62471). Setting to EOF.
Cluster 30154 out of range (64511 > 62471). Setting to EOF.
Cluster 30301 out of range (64511 > 62471). Setting to EOF.
Cluster 30449 out of range (64511 > 62471). Setting to EOF.
Cluster 30596 out of range (64511 > 62471). Setting to EOF.
Cluster 30746 out of range (64511 > 62471). Setting to EOF.
Cluster 30895 out of range (64511 > 62471). Setting to EOF.
Cluster 31045 out of range (64511 > 62471). Setting to EOF.
Cluster 31183 out of range (64511 > 62471). Setting to EOF.
Cluster 31323 out of range (64511 > 62471). Setting to EOF.
Cluster 31465 out of range (64511 > 62471). Setting to EOF.
Cluster 31608 out of range (64511 > 62471). Setting to EOF.
Cluster 31728 out of range (64511 > 62471). Setting to EOF.
Cluster 31850 out of range (64511 > 62471). Setting to EOF.
Cluster 31971 out of range (64511 > 62471). Setting to EOF.
Cluster 32092 out of range (64511 > 62471). Setting to EOF.
Cluster 32216 out of range (64511 > 62471). Setting to EOF.
Cluster 32341 out of range (64511 > 62471). Setting to EOF.
Cluster 32465 out of range (64511 > 62471). Setting to EOF.
Cluster 32590 out of range (64511 > 62471). Setting to EOF.
Cluster 32714 out of range (64511 > 62471). Setting to EOF.
Cluster 32838 out of range (64511 > 62471). Setting to EOF.
Cluster 32963 out of range (64511 > 62471). Setting to EOF.
Cluster 33087 out of range (64511 > 62471). Setting to EOF.
Cluster 33213 out of range (64511 > 62471). Setting to EOF.
Cluster 33338 out of range (64511 > 62471). Setting to EOF.
Cluster 33463 out of range (64511 > 62471). Setting to EOF.
Cluster 33590 out of range (64511 > 62471). Setting to EOF.
Cluster 33718 out of range (64511 > 62471). Setting to EOF.
Cluster 33848 out of range (64511 > 62471). Setting to EOF.
Cluster 33977 out of range (64511 > 62471). Setting to EOF.
Cluster 34105 out of range (64511 > 62471). Setting to EOF.
Cluster 34236 out of range (64511 > 62471). Setting to EOF.
Cluster 34367 out of range (64511 > 62471). Setting to EOF.
Cluster 34496 out of range (64511 > 62471). Setting to EOF.
Cluster 34626 out of range (64511 > 62471). Setting to EOF.
Cluster 34769 out of range (64511 > 62471). Setting to EOF.
Cluster 34913 out of range (64511 > 62471). Setting to EOF.
Cluster 35054 out of range (64511 > 62471). Setting to EOF.
Cluster 35198 out of range (64511 > 62471). Setting to EOF.
Cluster 35344 out of range (64511 > 62471). Setting to EOF.
Cluster 35493 out of range (64511 > 62471). Setting to EOF.
Cluster 35641 out of range (64511 > 62471). Setting to EOF.
Cluster 35767 out of range (64511 > 62471). Setting to EOF.
Cluster 35886 out of range (64511 > 62471). Setting to EOF.
Cluster 36000 out of range (64511 > 62471). Setting to EOF.
Cluster 36122 out of range (64511 > 62471). Setting to EOF.
Cluster 36256 out of range (64511 > 62471). Setting to EOF.
Cluster 36383 out of range (64511 > 62471). Setting to EOF.
Cluster 36507 out of range (64511 > 62471). Setting to EOF.
Cluster 36637 out of range (64511 > 62471). Setting to EOF.
Cluster 36782 out of range (64511 > 62471). Setting to EOF.
Cluster 36912 out of range (64511 > 62471). Setting to EOF.
Cluster 37042 out of range (64511 > 62471). Setting to EOF.
Cluster 37189 out of range (64511 > 62471). Setting to EOF.
Cluster 37315 out of range (64511 > 62471). Setting to EOF.
Cluster 37450 out of range (64511 > 62471). Setting to EOF.
Cluster 37590 out of range (64511 > 62471). Setting to EOF.
Cluster 37746 out of range (64511 > 62471). Setting to EOF.
Cluster 37909 out of range (64511 > 62471). Setting to EOF.
Cluster 38061 out of range (64511 > 62471). Setting to EOF.
Cluster 38186 out of range (64511 > 62471). Setting to EOF.
Cluster 38296 out of range (64511 > 62471). Setting to EOF.
Cluster 38431 out of range (64511 > 62471). Setting to EOF.
Cluster 38545 out of range (64511 > 62471). Setting to EOF.
Cluster 38653 out of range (64511 > 62471). Setting to EOF.
Cluster 38752 out of range (64511 > 62471). Setting to EOF.
Cluster 38873 out of range (64511 > 62471). Setting to EOF.
Cluster 38989 out of range (64511 > 62471). Setting to EOF.
Cluster 39114 out of range (64511 > 62471). Setting to EOF.
Cluster 39229 out of range (64511 > 62471). Setting to EOF.
Cluster 39353 out of range (64511 > 62471). Setting to EOF.
Cluster 39479 out of range (64511 > 62471). Setting to EOF.
Cluster 39604 out of range (64511 > 62471). Setting to EOF.
Cluster 39721 out of range (64511 > 62471). Setting to EOF.
Cluster 39823 out of range (64511 > 62471). Setting to EOF.
Cluster 39924 out of range (64511 > 62471). Setting to EOF.
Cluster 39925 out of range (64511 > 62471). Setting to EOF.
Cluster 40029 out of range (64511 > 62471). Setting to EOF.
Cluster 40133 out of range (64511 > 62471). Setting to EOF.
Cluster 40239 out of range (64511 > 62471). Setting to EOF.
Cluster 40341 out of range (64511 > 62471). Setting to EOF.
Cluster 40420 out of range (64511 > 62471). Setting to EOF.
Cluster 40500 out of range (64511 > 62471). Setting to EOF.
Cluster 40580 out of range (64511 > 62471). Setting to EOF.
Cluster 40659 out of range (64511 > 62471). Setting to EOF.
Cluster 40736 out of range (64511 > 62471). Setting to EOF.
Cluster 40816 out of range (64511 > 62471). Setting to EOF.
Cluster 40887 out of range (64511 > 62471). Setting to EOF.
Cluster 40958 out of range (64511 > 62471). Setting to EOF.
Cluster 41029 out of range (64511 > 62471). Setting to EOF.
Cluster 41099 out of range (64511 > 62471). Setting to EOF.
Cluster 41170 out of range (64511 > 62471). Setting to EOF.
Cluster 41240 out of range (64511 > 62471). Setting to EOF.
Cluster 41310 out of range (64511 > 62471). Setting to EOF.
Cluster 41380 out of range (64511 > 62471). Setting to EOF.
Cluster 41450 out of range (64511 > 62471). Setting to EOF.
Cluster 41520 out of range (64511 > 62471). Setting to EOF.
Cluster 41590 out of range (64511 > 62471). Setting to EOF.
Cluster 41662 out of range (64511 > 62471). Setting to EOF.
Cluster 41735 out of range (64511 > 62471). Setting to EOF.
Cluster 41807 out of range (64511 > 62471). Setting to EOF.
Cluster 41917 out of range (64511 > 62471). Setting to EOF.
Cluster 42022 out of range (64511 > 62471). Setting to EOF.
Cluster 42128 out of range (64511 > 62471). Setting to EOF.
Cluster 42230 out of range (64511 > 62471). Setting to EOF.
Cluster 42331 out of range (64511 > 62471). Setting to EOF.
Cluster 42432 out of range (64511 > 62471). Setting to EOF.
Cluster 42563 out of range (64511 > 62471). Setting to EOF.
Cluster 42695 out of range (64511 > 62471). Setting to EOF.
Cluster 42827 out of range (64511 > 62471). Setting to EOF.
Cluster 42962 out of range (64511 > 62471). Setting to EOF.
Cluster 43063 out of range (64511 > 62471). Setting to EOF.
Cluster 43151 out of range (64511 > 62471). Setting to EOF.
Cluster 43239 out of range (64511 > 62471). Setting to EOF.
Cluster 43321 out of range (64511 > 62471). Setting to EOF.
Cluster 43403 out of range (64511 > 62471). Setting to EOF.
Cluster 43479 out of range (64511 > 62471). Setting to EOF.
Cluster 43555 out of range (64511 > 62471). Setting to EOF.
Cluster 43847 out of range (64511 > 62471). Setting to EOF.
Cluster 43876 out of range (64511 > 62471). Setting to EOF.
Cluster 44167 out of range (64511 > 62471). Setting to EOF.
Cluster 44194 out of range (64511 > 62471). Setting to EOF.
Cluster 44485 out of range (64511 > 62471). Setting to EOF.
Cluster 44515 out of range (64511 > 62471). Setting to EOF.
Cluster 44780 out of range (64511 > 62471). Setting to EOF.
Cluster 44803 out of range (64511 > 62471). Setting to EOF.
Cluster 45124 out of range (64511 > 62471). Setting to EOF.
Cluster 45159 out of range (64511 > 62471). Setting to EOF.
Cluster 45490 out of range (64511 > 62471). Setting to EOF.
Cluster 45525 out of range (64511 > 62471). Setting to EOF.
Cluster 45844 out of range (64511 > 62471). Setting to EOF.
Cluster 45879 out of range (64511 > 62471). Setting to EOF.
Cluster 46197 out of range (64511 > 62471). Setting to EOF.
Cluster 46231 out of range (64511 > 62471). Setting to EOF.
Cluster 46485 out of range (64511 > 62471). Setting to EOF.
Cluster 46503 out of range (64511 > 62471). Setting to EOF.
Cluster 46763 out of range (64511 > 62471). Setting to EOF.
Cluster 46785 out of range (64511 > 62471). Setting to EOF.
Cluster 47063 out of range (64511 > 62471). Setting to EOF.
Cluster 47089 out of range (64511 > 62471). Setting to EOF.
Cluster 47382 out of range (64511 > 62471). Setting to EOF.
Cluster 47414 out of range (64511 > 62471). Setting to EOF.
Cluster 47723 out of range (64511 > 62471). Setting to EOF.
Cluster 47759 out of range (64511 > 62471). Setting to EOF.
Cluster 48078 out of range (64511 > 62471). Setting to EOF.
Cluster 48112 out of range (64511 > 62471). Setting to EOF.
Cluster 48445 out of range (64511 > 62471). Setting to EOF.
Cluster 48484 out of range (64511 > 62471). Setting to EOF.
Cluster 48756 out of range (64511 > 62471). Setting to EOF.
Cluster 48780 out of range (64511 > 62471). Setting to EOF.
Cluster 49038 out of range (64511 > 62471). Setting to EOF.
Cluster 49058 out of range (64511 > 62471). Setting to EOF.
Cluster 49318 out of range (64511 > 62471). Setting to EOF.
Cluster 49339 out of range (64511 > 62471). Setting to EOF.
Cluster 49590 out of range (64511 > 62471). Setting to EOF.
Cluster 49609 out of range (64511 > 62471). Setting to EOF.
Cluster 49893 out of range (64511 > 62471). Setting to EOF.
Cluster 49921 out of range (64511 > 62471). Setting to EOF.
Cluster 50190 out of range (64511 > 62471). Setting to EOF.
Cluster 50214 out of range (64511 > 62471). Setting to EOF.
Cluster 50484 out of range (64511 > 62471). Setting to EOF.
Cluster 50509 out of range (64511 > 62471). Setting to EOF.
Cluster 50779 out of range (64511 > 62471). Setting to EOF.
Cluster 50804 out of range (64511 > 62471). Setting to EOF.
Cluster 51073 out of range (64511 > 62471). Setting to EOF.
Cluster 51097 out of range (64511 > 62471). Setting to EOF.
Cluster 51367 out of range (64511 > 62471). Setting to EOF.
Cluster 51391 out of range (64511 > 62471). Setting to EOF.
Cluster 51643 out of range (64511 > 62471). Setting to EOF.
Cluster 51664 out of range (64511 > 62471). Setting to EOF.
Cluster 51916 out of range (64511 > 62471). Setting to EOF.
Cluster 51938 out of range (64511 > 62471). Setting to EOF.
Cluster 52191 out of range (64511 > 62471). Setting to EOF.
Cluster 52214 out of range (64511 > 62471). Setting to EOF.
Cluster 52470 out of range (64511 > 62471). Setting to EOF.
Cluster 52494 out of range (64511 > 62471). Setting to EOF.
Cluster 52743 out of range (64511 > 62471). Setting to EOF.
Cluster 52766 out of range (64511 > 62471). Setting to EOF.
Cluster 52880 out of range (64511 > 62471). Setting to EOF.
Cluster 52994 out of range (64511 > 62471). Setting to EOF.
Cluster 53103 out of range (64511 > 62471). Setting to EOF.
Cluster 53219 out of range (64511 > 62471). Setting to EOF.
Cluster 53329 out of range (64511 > 62471). Setting to EOF.
Cluster 53421 out of range (64511 > 62471). Setting to EOF.
Cluster 53522 out of range (64511 > 62471). Setting to EOF.
Cluster 53639 out of range (64511 > 62471). Setting to EOF.
Cluster 53780 out of range (64511 > 62471). Setting to EOF.

```

Seems to me like there is something wrong with a lot of the clusters and fsck ignores them (probably doesn't change them since the card still works in my camera). And those clusters must be containing my pictures but Linux refuses to read them but the Canon just goes ahead and reads it anyway.

---

### Post by tgalati4 on 2009-08-20
Well, I think you got heavy-handed.  Jo Mama seems toast.

I'm speculating, but the fsck.vfat tried to fix errors and made the problem worse.

Before you used the reader, did you try plugging in the camera with the card?

If so, did a dialog show up asking how would you like to handle these digital pictures?

Sometimes the in-camera USB reader works better than an external/internal USB card reader.  Some cards work better than others with certain card readers.

If the card was never previously formatted under linux then it should be either FAT16 or FAT32 without a partition table.  This makes fsck more difficult.

Testdisk will try to repair the FAT, photorec will scan the sectors for jpg headers and follow the sector string--hopefully recovering the file in the process.

Can you see the pictures using the playback function in the camera?  If so have you gone through each one to make sure the camera can read it?

Find an external USB disk.  Make a 2.2 GB partition on it.  Let's call this /dev/sde1
I would do a mass copy:

sudo cp /dev/sdd1 /dev/sde1

See if you can find the photos on /dev/sde1.

The problem with dd is that it does a block-by-block copy and we want a logical copy letting the kernel figure out each device's characteristics.

---

### Post by benne on 2009-08-21
I am able to browse the pictures on the camera with the in-camera playback. Ive checked every single photo and it seems to add up. This makes me think that the card is not toast. 

Yes, gnome's device awareness popped up and asked me what i wanted to do with the photos, but then gave me the error i wrote above. 

I think the filesystem is FAT16, but it might be FAT32. The card is relatively new, I don't remember but I think it was preformatted. Otherwise I formatted it with the camera. 

I have had trouble connecting the camera directly, I will try to get hold of another camera and try with that one. 

Thanks for the tip though. Ill give it a try and report back with results.

---

### Post by tgalati4 on 2009-08-21
Immediately after plugging the camera in:

dmesg | tail -30

---

### Post by benne on 2009-08-21
> **tgalati4 said:**
> Immediately after plugging the camera in:

dmesg | tail -30

Its still the same..

```
[12594.748715] usb 1-1: new high speed USB device using ehci_hcd and address 4
[12594.905170] usb 1-1: configuration #1 chosen from 1 choice
```

Only these lines. No more, no less.

---

### Post by benne on 2009-08-21
Copied to a usb drive, and the drive now behaves excatly like the memory card. Gnome tried to mount it as "JO NAMA" and refues to open it. 

fsck.msdos ouptuts this a couple of hundred times:

```
/DCII/210CAJOJ/k&#65533;E&#65533;/\020jJ.\226&#65533;m
  Bad file name.
  Auto-renaming it.
  Renamed to 996\0000000.\000&#65533;m
/DCII/210CAJOJ/&#65533;&#65533;\204:\037K\213&#65533;.&#65533;\203
  Bad file name.
  Auto-renaming it.
  Renamed to 997\0000000.\000\203
/DCII/210CAJOJ/&#65533;C&#65533;\220>Ryc.&#65533;c\031
  Bad file name.
  Auto-renaming it.
  Renamed to 998\0000000.\000c\031
/DCII/210CAJOJ/\201\212+&#65533;r&#65533;\016Y.&#65533;y&#65533;
  Bad file name.
  Auto-renaming it.
  Renamed to 999\0000000.\000y&#65533;
/DCII/210CAJOJ/GZ&#65533;\212\013\223+c.n8&#65533;
  Bad file name.
  Auto-renaming it.
Too many files need repair.

```

Mounting it and trying to ls it. 
```
root@bk-laptop:/media# mount /dev/sdb1 1
root@bk-laptop:/media# cd 1
root@bk-laptop:/media/1# ls
ls: cannot access dcii: Input/output error
dcii
root@bk-laptop:/media/1# ls dcii 
ls: cannot access dcii: Input/output error
```

The card still works fine in the camera

---

### Post by tgalati4 on 2009-08-21
When you copied to a USB drive did you use dd or cp?

Also, buried deep in your camera's connectivity settings is something called USB Mode.  Try using both modes and make sure the camera is in "Playback mode", plug in into computer with USB, then power on the camera.  Post the dmesg | tail -30

Also, can you zoom into the photo's on the camera.  Have you confirmed that you are viewing the actual photo's and not small thumbnails stored elsewhere on the card?

---

### Post by benne on 2009-08-21
I have thought of that. I can zoom in - i am viewing the actual photographs. There are a few raw files and i have confirmed that they also are real raw files (not thumbnails) and full 8 MP. So the photos are there, not just some thumbnails. 

I both tried dd (as described in my first post) and cp as you described. I now have a USB stick that is a replica of the card. 

I bought a new memory card reader. This one manges to read my other cards but not this one. It still gives filesystem panic in the dmesg. 

My camera is a Canon EOS 20D. I supports two file transfer modes, "Normal" and "PTP" (called Communication) . Not much happens with i use PTP but "Normal" results in the error described above. I would have thought that "normal" was mass storage mode. Gnome's device awareness pops up and asks me if i want to view the files and opens Nautilus at gphoto2://[usb:001,023]/ . 

I have also tried my old Canon EOS 400D with the same results, except it doesnt give me an error, just shows as a empty card, still noting "279 MB free" though. 

Here is the dmesg | tail -30. Camera on, Communication in Normal. This is a pro camera and has no playback mode. 

```
[30616.372226] usb 1-6.2: new high speed USB device using ehci_hcd and address 26
[30616.533581] usb 1-6.2: configuration #1 chosen from 1 choice

```

I am completely baffled.

---

### Post by benne on 2009-08-21
The problem is solved. Thank you for your help.

In case somebody else is unlucky enough to stubmle into this problem, here is how I solved it. 

Firstly, there seems to be something wrong with my original card reader. I bought a new one to isolate the problem and this one works. 

I made a new dd image of the card, so I can work with that one and not the card itself. 
```
dd if=/dev/sdc1 of=~/memcard.bin
```

Then I ran fsck on it. I didn't run fsck.msdos, just fsck. According to the man pages these are two different comands. fsck.msdos is actually dosfsck. 

```
# fsck -a ~/memcard.bin 
fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
Cluster 0 out of range (64511 > 62471). Setting to EOF.
Cluster 1 out of range (64511 > 62471). Setting to EOF.
Cluster 151 out of range (64511 > 62471). Setting to EOF.
Performing changes.
```

Like magic - a totally different output. I dont know how fsck.msdos would have reacted. But for comparasion I ran fsck on the old file and it behaved like before. Thus i draw the conclution that the card reader is to be blamed. 

Next is to mount the binary image of the card. 

```
# mount ~/memcard.bin /media/tmp/ -o loop
```

And voila!
```
# ls /media/tmp/dcim/
249canon  250canon  253canon  254canon  255canon  256canon

```

My semester pictures are saved!

Thank you for the troubleshooting help.

---

### Post by tgalati4 on 2009-08-22
That's good news.  fsck will try to determine the filesystem type and run the appropriate check.  It is not always successful.  What is interesting is that both fsck.vfat and fsck.msdos both point to dosfsck.

ls -la /sbin/fs*

I always thought that when fsck encountered a FAT16 or FAT32 filesystem that it invoked fsck.vfat which is symbolically-linked to dosfsck.

There are a lot of switches to fiddle with in dosfsck and it's an old program, 1997 vintage.

Modern flash cards contain reserve areas for writing badblocks to.  It's possible that the card reader was incorrectly reading the size of the filesystem leading to strange errors.  The fsck corrected those inconsistencies without destroying your pictures.

The PTP (point-to-point?) mode is used to control the camera using a long USB cable for remote-control photography.  I have a powershot A70 that I've played in both Mac and Linux.  It's useful for long, nighttime exposures, astro stuff and for wildlife blinds.

Be careful when formatting CF cards in linux.  If you don't keep the head, cylinder, sector count correct for your card, you can make it unreadable.  Best to format it in Windows or in-camera.  Make a note of the head, cyclinder, sector count for each type of card, because you may need it in the future.

I've gotten the best performance from 32-bit pcmcia CF card readers--for a laptop.  They are more expensive than the 16-bit pcmcia readers, but they are much faster.

My built-in desktop CF reader (2006 vintage) has problems with 2 GB and 4 GB CF cards, but my HP photosmart printer with a reader works OK with larger cards.  It's just much slower over USB.

That's quite clever to run fsck on a binary image of the card as a local file.  Linux is always full of surprises.

---

### Post by benne on 2009-08-22
I also thought that fsck would do that - but I didn't see anything about this behavior in the man page. I think dosfsck is getting a bit old, but its still a handsome brute. :-)

I didn't know about the reserve blocks on flash drives. This seems to make sense though, it would explain why it was always pointing to the wrong address. 

I saw one of those 32bit readers in the store yesterday when i bought the reader. It was at a whopping price of 14.000 ISK when the plastic blue thing I bought was more sensibly priced at 2.300 ISK. 

Oh and to be completely off topic - how did you control the camera through PTP mode in Linux? This is very interesting. Didn't think that this would be possible since the Canon camera hardware isn't exactly what you'd call well-documented.

---

### Post by MaxIBoy on 2009-08-22
Someone once demonstrated PTP mode with his Mac, but he never told me how he did it.

Some quick googling turned this up:
[http://ptp.sourceforge.net/](http://ptp.sourceforge.net/)

---

