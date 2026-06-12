---
title: "bcm43xx and more than 1 gig of ram"
date: 2006-06-01
forum: General Help
---

### Post by djsamsel on 2006-06-01
a week ago i was finally able to get the broadcom 4306 wireless card working on my gateway notebook. i think i remember that the driver does not work if there is 1 or more gigs of ram installed on the system. however, right now i can't find that statement anywhere in the wiki. so i installed a gig chip in the system (total is 1.25 gigs). the blue wireless light still comes on, but i'm not connecting to the wireless router anymore. does anyone know if there is a work around? thanks, doug

---

### Post by bollix47 on 2006-06-01
Anything [here]("http://www.ubuntuforums.org/showthread.php?t=185650") help?

---

### Post by djsamsel on 2006-06-01
thanks, but i don't think so. i had already used fwcutter and the wireless worked great with gnome connection manager. it's just that now that i added the gig ram, the computer does not even see the wireless connections. the light is still on saying that the wireless card is active, but no connection. if i do

sudo iwconfig eth0
 IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

typing in sudo iwconfig eth0 ap any has no affect. any other suggestions?

---

### Post by bollix47 on 2006-06-01
Have you read thru [this]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-e70dd6b5c57894d32e3eddc4f3e21d7d6d02230f")?

---

### Post by djsamsel on 2006-06-01
[QUOTE=bollix47]Have you read thru [this]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx#head-e70dd6b5c57894d32e3eddc4f3e21d7d6d02230f")?[/QUOTE]


yes, thank you, i have. that's orginally how i got it running. i used the native driver. since i added the extra RAM is when the problem developed.

---

### Post by bollix47 on 2006-06-01
The > 1 gig problem is mentioned [here]("http://ubuntuforums.org/showpost.php?p=1059845&postcount=264")

---

### Post by djsamsel on 2006-06-01
[QUOTE=bollix47]The > 1 gig problem is mentioned [here]("http://ubuntuforums.org/showpost.php?p=1059845&postcount=264")[/QUOTE]


thanks, i had found that and tried everything suggested in his tag line, but no change. actually, i took the 1 meg simm out for awhile and it took some fiddeling to get the driver back up again. i then updated everything i could, put the simm back in and it worked for about 20 minutes at the office. however, now that i'm home it's quit working again. does anyone have this card working with more than 1 gig of ram?

---

### Post by joshrobinson on 2006-06-01
[QUOTE=djsamsel]thanks, i had found that and tried everything suggested in his tag line, but no change. actually, i took the 1 meg simm out for awhile and it took some fiddeling to get the driver back up again. i then updated everything i could, put the simm back in and it worked for about 20 minutes at the office. however, now that i'm home it's quit working again. does anyone have this card working with more than 1 gig of ram?[/QUOTE]

i have an even 1gig of ram.. a single 1024.. and the same wireless.. i never tried the native driver, have you tried using ndiswrapper for your wireless?

---

### Post by cwmaxson on 2006-06-01
Hola,
I had the same problem, with the same BCM card.  I just limited mine to 1 gig for now and everything works smooth.  Sorry if that's not what you want to hear.

---

### Post by quad3d@work on 2006-10-20
I had 1.5G of RAM before and it worked w/ native driver running 32-bit.

---

