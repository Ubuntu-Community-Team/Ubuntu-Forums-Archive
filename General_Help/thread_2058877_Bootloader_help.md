---
title: "Bootloader help"
date: 2012-09-16
forum: General Help
---

### Post by coolsway on 2012-09-16
Basically, I installed Ubuntu on a different partition, from my windows.
Then, when I turned on my computer, it had the Ubuntu boot manager. I installed easyBCD. Now, when I turned on my computer, here is what happens:

to go into Windows: 
Ubuntu Bootloader(select windows)--> Windows Bootloader(select windows)

to go into Ubuntu:
Ubuntu bootloader(select Ubuntu)

Then, I installed grub manager in Ubuntu, and made it so it will automatically go into the windows when I turn on my computer, thinking that if it goes into windows, I can select either Ubuntu or windows to boot into.

Then, when I tried to get into Ubuntu, it will bring me back to the Windows bootloader(because now, when I go to Ubuntu, it will go to the bootloader, which automatically go into Windows bootloader.

Then, I decided I didn't have anything in Ubuntu anyways, and re-installed. So now,it is basically the ubuntu booloader then the windows bootloader.

Basically, if that was confusing, I need the windows bootloader to come before the Ubuntu bootloader. After, I plan to hide the ubuntu bootloader. How would I do that? 

Thanks

---

### Post by andrew3 on 2012-09-16
It sounds like you want to install GRUB2 on the PBR (partition boot record) instead of the MBR.

Some instructions here:
[http://askubuntu.com/questions/159492/installing-12-04s-boot-loader-on-the-partition-boot-record](http://askubuntu.com/questions/159492/installing-12-04s-boot-loader-on-the-partition-boot-record)

It sounds like you have GRUB2 installed on the MBR at the moment. In this case, you will need to reinstall the Windows stage 1 bootloader on the MBR.

PS. When I dual booted I tried doing this, but for some reason I could  never get it working. I think it was because of my BCD though. I just  installed GRUB2 on the MBR instead.


You're other option could be changing the order of the GRUB2 bootloader, so Windows comes before Ubuntu. Check out these instructions for doing so:
[https://shadesfgray.wordpress.com/2010/01/31/change-grub-boot-order-ubuntu-9-10/](https://shadesfgray.wordpress.com/2010/01/31/change-grub-boot-order-ubuntu-9-10/)

IMHO leaving GRUB2 on the MBR would be the more sensible option. :)

---

### Post by coolsway on 2012-09-16
> **andrew3 said:**
> It sounds like you want to install GRUB2 on the PBR (partition boot record) instead of the MBR.

Some instructions here:
[http://askubuntu.com/questions/159492/installing-12-04s-boot-loader-on-the-partition-boot-record](http://askubuntu.com/questions/159492/installing-12-04s-boot-loader-on-the-partition-boot-record)

It sounds like you have GRUB2 installed on the MBR at the moment. In this case, you will need to reinstall the Windows stage 1 bootloader on the MBR.

PS. When I dual booted I tried doing this, but for some reason I could  never get it working. I think it was because of my BCD though. I just  installed GRUB2 on the MBR instead.


You're other option could be changing the order of the GRUB2 bootloader, so Windows comes before Ubuntu. Check out these instructions for doing so:
[https://shadesfgray.wordpress.com/2010/01/31/change-grub-boot-order-ubuntu-9-10/](https://shadesfgray.wordpress.com/2010/01/31/change-grub-boot-order-ubuntu-9-10/)

IMHO leaving GRUB2 on the MBR would be the more sensible option. :)

I'm confused, there are so many things I am supposed to do. What one did you do?

---

### Post by andrew3 on 2012-09-16
I installed GRUB2 on the MBR, which is default.

  Sorry about being so confusing. You'd be better off following these instructions to change the order of the GRUB2 bootloader:

  [https://shadesfgray.wordpress.com/2010/01/31/change-grub-boot-order-ubuntu-9-10/](https://shadesfgray.wordpress.com/2010/01/31/change-grub-boot-order-ubuntu-9-10/)

  Just use sudo or root account so that 30_os-prober is renamed to 10_os-prober and rename 10_linux to 30_linux.

  Then do sudo update-grub and reboot. It *should* hopefully work. :)

---

### Post by coolsway on 2012-09-16
> **andrew3 said:**
> I installed GRUB2 on the MBR, which is default.

  Sorry about being so confusing. You'd be better off following these instructions to change the order of the GRUB2 bootloader:

  [https://shadesfgray.wordpress.com/2010/01/31/change-grub-boot-order-ubuntu-9-10/](https://shadesfgray.wordpress.com/2010/01/31/change-grub-boot-order-ubuntu-9-10/)

  Just use sudo or root account so that 30_os-prober is renamed to 10_os-prober and rename 10_linux to 30_linux.

  Then do sudo update-grub and reboot. It *should* hopefully work. :)

how do you rename it? I typed in cd into /etc/grub.d then ls, but there is no option to rename it. Do I have to tpye a different code to do that?
Edit: never mind, i just did sudo mv (original)(changed)

---

### Post by gnometorule on 2012-09-16
This is an excellent grub tutorial (and if you click around, he has a similarly good grub2 tutorial). You're currently tapping in the dark in reasonably unpleasant territory, and I warmly suggest you first get to understand the basics of these programs before meddling with them. N.B., grub is 'easier' and pretty much used in Linux distos other than Ubuntu, with Ubuntu being the only  major grub2 distro. So I suggest you read the grub tutorial first, then the other.

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

After you digested that, do come back if you cannot resolve the issues.

---

