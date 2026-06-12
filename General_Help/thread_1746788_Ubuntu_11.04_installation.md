---
title: "Ubuntu 11.04 installation"
date: 2011-05-02
forum: General Help
---

### Post by Iqbal_ on 2011-05-02
Hi,

Configuration of the laptop is:
64bits, core 2 duo intel processor, nvidia motheboard.
dual boot with Vista and ubuntu 9.10
4GB RAM and 500GB HDD

I have been using ubuntu 9.10. It is running smoothly. I have installed ubuntu 9.10 several time without any problem.

Recently I was installing ubuntu 11.04. The laptop reads the CD, ubuntu screen comes up then it only shows empty ubuntu desktop with a live mouse pointer. From this point, it does not move forward.

I faced the same problem in installing 10.04 and 11.10.

How to install ubuntu 11.04?

---

### Post by Naike on 2011-05-02
ubuntu is **** it never worked for me

---

### Post by 73ckn797 on 2011-05-02
You have not said whether you have checked the md5sums of the downloaded iso and then performed the Live CD self test after burning the iso. All of the problems that I have experienced have been due to the md5sums or a sudden hardware issue.

Ubuntu 8.10 was the exception for me. It was not the best version in my experience. Each person experiences different issues.

I have deleted MS Windows on both of my computers. Ubuntu does all that I need. There are those who seem to have no success with Ubuntu, as already stated in the last post here.

---

### Post by Iqbal_ on 2011-05-02
Yes, I have checked md5sum of the downloaded file. The iso was burnt on the lowest speed using ubuntu 9.10- Brasero. It was also correct.

---

### Post by 73ckn797 on 2011-05-02
Will 9.10 still load up? If not then maybe a dirty drive unless you were able to burn using the laptop drive. Possible to consider a memory issue. I just went through that kind of problem. The disks would burn and check out good but would always give I/O errors or quit the installer when formatting the drive while installing. Multiple disks, CD/DVD drives and 4 hard drives tried. Discovered one of the memory modules was bad. Removed the suspect and all works fine now.

---

### Post by Iqbal_ on 2011-05-03
Hi,
I started with live CD. When the first screen came, with two icons in the bottom I pressed spacebar. Then i was given to choose language and booting options. Before choosing the booting option-the first option of booting from CD without change to computer, I pressed F6 for boot options. I selected first option acpi=off, pressed Esc and select the first option. I could run ubuntu 11.04 from Live CD. I could also connect to internet. But when I shut down the laptop, power did not switch-off. I had to press power button manually to shut down the laptop.

So please explain what is acpi=off? Why was not the laptop shutting down until I pressed power button manually? If I install ubuntu 11.04 using this boot option, would I be able to use ubuntu 11.04 smoothly?

---

### Post by 73ckn797 on 2011-05-03
> **Iqbal_ said:**
> Hi,
I started with live CD. When the first screen came, with two icons in the bottom I pressed spacebar. Then i was given to choose language and booting options. Before choosing the booting option-the first option of booting from CD without change to computer, I pressed F6 for boot options. I selected first option acpi=off, pressed Esc and select the first option. I could run ubuntu 11.04 from Live CD. I could also connect to internet. But when I shut down the laptop, power did not switch-off. I had to press power button manually to shut down the laptop.

So please explain what is acpi=off? Why was not the laptop shutting down until I pressed power button manually? If I install ubuntu 11.04 using this boot option, would I be able to use ubuntu 11.04 smoothly?

Here: [http://www.google.com/#sclient=psy&hl=en&biw=1280&bih=798&source=hp&q=acpi+off+ubuntu&aq=1&aqi=g5&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=822bf32b5c0e0691](http://www.google.com/#sclient=psy&hl=en&biw=1280&bih=798&source=hp&q=acpi+off+ubuntu&aq=1&aqi=g5&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=822bf32b5c0e0691)

Here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Here: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

---

### Post by Iqbal_ on 2011-05-09
Hi,
After booting from Live CD, I pressed F6 (Boot Options) and chosen nomodeset. Then installed the operating system. Now it is running fine till now. 

I was able to connect to internet also using mobile. I have not tested other features by now.

---

