---
title: "LastPass Sesame and Pocket problems"
date: 2012-02-08
forum: General Help
---

### Post by Welly Wu on 2012-02-08
I installed Ubuntu 11.10 64 bit earlier today using the Alternative Installation .ISO file that I burned onto a CD-R. I setup full disk encryption using LUKS/LVM and AES-CBC mode 256 bits SHA-256 hash algorithm. I am a LastPass Premium subscriber. I downloaded the 32 and 64 bit versions of LastPass Pocket and Sesame today and they won't run at all. I typed in sudo apt-get install ca-certificates and it tells me that I have the latest version installed. Whenever I click on LastPass Pocket or Sesame, nothing happens. I checked the file permissions and both are set to execute. How do I get LastPass Pocket and Sesame to work on Ubuntu 11.10 64 bit?

---

### Post by Welly Wu on 2012-02-09
I had to install libssl 0.98. Then, I had to open up port 443 for outgoing traffic in my GUFW firewall configuration. Next, I had to type in chmod +x sesame_x64 and pocket_x64. Finally, it works. I can get LastPass Pocket and Sesame to work if I use the x64 bit versions.

---

