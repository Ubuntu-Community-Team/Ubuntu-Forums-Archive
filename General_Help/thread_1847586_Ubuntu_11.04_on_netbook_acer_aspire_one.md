---
title: "Ubuntu 11.04 on netbook acer aspire one"
date: 2011-09-21
forum: General Help
---

### Post by tnkie on 2011-09-21
Hi I'm having some pretty major problems with 11.04, despite that acer aspire one's are supposedly certified for this release. 

I initially was unable to run unity at all, however following this guide:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

specifically:

```
sudo add-apt-repository ppa:gma500/emgd  sudo apt-get update sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf sudo emgd-xorg-conf
```Unity began to work, but still extrely laggy. The bar at the top is very blurry and the icons on the launch bar pixellated. Also the system frequently reports an there has been an error, and asks me to submit a report.

I am using An Acer aspire one ZA3. I have no commitment to keeping 11.04 if there isn't a solution, although I would rather have the latest Ubuntu running. If there is a better performing version of Ubuntu someone can recommend then I may use that instead.

Thank in advance.

Edit: the error is "System program problem detected".

---

### Post by scarleo on 2011-09-21
Sounds more like something went wrong during install. Verify your download (HOWTO: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) and reinstall. I'm running 11.04 on Aspire One ZG5 without any problems whatsoever. Also keep an extra lookout for any error messages during install.

---

### Post by tnkie on 2011-09-21
> **scarleo said:**
> Sounds more like something went wrong during install. Verify your download (HOWTO: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) and reinstall. I'm running 11.04 on Aspire One ZG5 without any problems whatsoever. Also keep an extra lookout for any error messages during install.

Thanks for your reply. Did you have any problems with your video card at all, or was everything OK "out of the box"?

I will try a reinstall if necessary a little later, until then any other experience or suggestions are welcome!

Cheers.

---

### Post by scarleo on 2011-09-21
Everything was OK out of the box after verifying that I had correct MD5 sum. I never had a corrupted download first and it puzzled me for a while but after getting a correct download it was smooth as silk, everything working out of the box, even built in 3G modem :)

Did you "Try Ubuntu" from CD/USB first? Did you have the same problem while testing it?

---

### Post by tnkie on 2011-09-21
> **scarleo said:**
> Everything was OK out of the box after verifying that I had correct MD5 sum. I never had a corrupted download first and it puzzled me for a while but after getting a correct download it was smooth as silk, everything working out of the box, even built in 3G modem :)

Did you "Try Ubuntu" from CD/USB first? Did you have the same problem while testing it?

I'm guessing it would have sent me to the classic desktop, so I wouldn't have seen unity. I'm gonna reinstall shortly (:popcorn:)  so I'll check that, we'll see how it goes!

---

