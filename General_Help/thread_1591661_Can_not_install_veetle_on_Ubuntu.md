---
title: "Can not install veetle on Ubuntu"
date: 2010-10-09
forum: General Help
---

### Post by htunnayshin on 2010-10-09
Hi,

I want to install veetle in my ubuntu. I have tried everything I could, but no success.Whenever I typed in sudo sh veetle-xxxxx-linux-install.sh (xxxxx:version), and then my password, in the terminal, it always said "can't open the file". Of course, I saved the file in the download first, and made sure allow excutable file box checked. I am new with linux. I am currently reading a book "ubuntu for beginner to professional", I hope it will help. If anyone can help me, please help.

Thank you,

---

### Post by techdude3177 on 2010-10-09
I downloaded the application just now and was able to install with no issues. If you downloaded this into your Downloads folder the command should look like this:


```
sudo ./Downloads/veetle-0.9.17-linux-install.sh
```

---

### Post by htunnayshin on 2010-10-09
> **techdude3177 said:**
> I downloaded the application just now and was able to install with no issues. If you downloaded this into your Downloads folder the command should look like this:


```
sudo ./Downloads/veetle-0.9.17-linux-install.sh
```


Thank you for very quick reply. This is what I got after entering your code. Is it because the brownser, I used google chrome-I found it a bit faster than swiftfox.

sudo: ./downloads/veetle-0.9.17-linux-install.sh: command not found

---

### Post by htunnayshin on 2010-10-09
> **htunnayshin said:**
> Thank you for very quick reply. This is what I got after entering your code. Is it because the brownser, I used google chrome-I found it a bit faster than swiftfox.

sudo: ./downloads/veetle-0.9.17-linux-install.sh: command not found

Hi,

This is me again for whoever replied my first thread. As I said after entering your code in terminal, and got command not found: as above.

Then, I tried out using "Swiftfox" as brownser and went to veetle tv website. I was able to watch everything there, but with firefox, and google chrome. Therefore, I should conclude that I do not have veetle software installed in my computer, since when I used firefox and chrome, veetle tv asked me to download and install the software-which I have not got it successfully, but for SWIFTFOX, I think it doesn't need the veetle software in order to be able to watch. Is that correct? I am not only trying to be able to watch it, but,also, part of it, want to learn too.

---

### Post by Mobidoy on 2010-10-09
You have to make it an executable, 

```
sudo chmod +x ./Downloads/veetle-0.9.17-linux-install.sh
```

Then run it:

```
sudo ./Downloads/veetle-0.9.17-linux-install.sh
```

---

### Post by htunnayshin on 2010-10-09
> **Mobidoy said:**
> You have to make it an executable, 

```
sudo chmod +x ./Downloads/veetle-0.9.17-linux-install.sh
```

Then run it:

```
sudo ./Downloads/veetle-0.9.17-linux-install.sh
```



I can help. The problem is I don't have credit card. I hope I will be able to find some alternative way!

---

### Post by Mobidoy on 2010-10-09
You dont need a credit card, I just installed it too and it worked... 

Type the commands I gave you respecting the case (small letters and capital letters) and you should be set...

verify and type here in which folder you have downloaded the file.

---

### Post by gwinkleman on 2010-10-17
> **Mobidoy said:**
> You have to make it an executable, 

```
sudo chmod +x ./Downloads/veetle-0.9.17-linux-install.sh
```

Then run it:

```
sudo ./Downloads/veetle-0.9.17-linux-install.sh
```

Mobidoy, this worked perfectly! Thanks for me letting watch the NFL on my computer at school! ha

---

### Post by Atiq Choudhry on 2010-11-22
> **Mobidoy said:**
> You have to make it an executable, 

```
sudo chmod +x ./Downloads/veetle-0.9.17-linux-install.sh
```

Then run it:

```
sudo ./Downloads/veetle-0.9.17-linux-install.sh
```
It worked perfectly! Many thanks for your help.

---

### Post by gaycheckml on 2011-02-16
I get this error:

> Decoder unpacked - Using for package extraction
./Downloads/veetle-0.9.17-linux-install.sh: fork: Cannot allocate memory

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error is not recoverable: exiting now

Veetle Installed Successfully.

You can now browse our video-web at [http://www.veetle.com](http://www.veetle.com)


But when I go to veetle.com I have to reinstall again, I am in a loop.

Using  Xubuntu 9.10

---

### Post by _shake on 2011-08-06
> **Mobidoy said:**
> You dont need a credit card, I just installed it too and it worked... 

Type the commands I gave you respecting the case (small letters and capital letters) and you should be set...

verify and type here in which folder you have downloaded the file.

This worked after hours of failure with other methods, registered to say thanks. The premier league starts tomorrow :popcorn:

---

### Post by gordintoronto on 2011-08-06
> **htunnayshin said:**
> Thank you for very quick reply. This is what I got after entering your code. Is it because the brownser, I used google chrome-I found it a bit faster than swiftfox.

sudo: ./downloads/veetle-0.9.17-linux-install.sh: command not found

Linux plays attention to upper and lower case. Downloads and downloads are completely different places.

---

### Post by owlkohaulic on 2011-09-07
if you want to install veetle on Ubuntu do this. i know it works with Firefox.

download this file to downloads folder and extract it.click on the install file and choose run in terminal it only takes a few seconds and its done.now you can watch veetle in firefox with no audio issues.make sure you do not already have veetle installed.

[http://veetle.com/download.php/veetle-0.9.17plus.tgz](http://veetle.com/download.php/veetle-0.9.17plus.tgz)

been trying to get it to work with the opera browser but no luck yet.

---

### Post by PremiumG on 2012-09-08
Anyone have luck with installing veetle HD on Chromium in Lubuntu 64-bit?

---

