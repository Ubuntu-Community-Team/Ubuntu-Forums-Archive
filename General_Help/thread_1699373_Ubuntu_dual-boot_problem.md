---
title: "Ubuntu dual-boot problem"
date: 2011-03-03
forum: General Help
---

### Post by Timos798 on 2011-03-03
Hey everybody,
I installed Ubuntu as a dual-boot with windows 7, but when I boot Ubuntu a black screen comes up asking me to type in my my username and password, but after I do it stays at the black screen, and has lots of white writing. I didn't read what the writing says, but it is something about running commands using "sudo." Can anyone tell me what is going ona nd how to fix it?

---

### Post by JDCoffey on 2011-03-03
We came into the same problem in my class on ubuntu my instructor said to reinstall and it should be fine but if you feel brave look up a list of sudu commands to start it with you can find them anywhere on the web

---

### Post by Timos798 on 2011-03-03
> **JDCoffey said:**
> We came into the same problem in my class on ubuntu my instructor said to reinstall and it should be fine but if you feel brave look up a list of sudu commands to start it with you can find them anywhere on the web
Ah right thanks, I just wished I knew what caused it, oh well. It looks a lot like the DOS interface right?

---

### Post by oldfred on 2011-03-03
You have booted and then logged into the terminal mode, which probably means you have a video issue.

Sometimes this works:
startx
#or now preferred, I have seen all of these as preferred but do not know if one is better or not.
sudo service gdm start

If it does not work:
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

---

### Post by Timos798 on 2011-03-04
I "fixed" the problem. I just re-installed Ubuntu, unsuccessfully. It's just gone back to the problem i had in the previous thread.

Thank sa lot guys.

---

