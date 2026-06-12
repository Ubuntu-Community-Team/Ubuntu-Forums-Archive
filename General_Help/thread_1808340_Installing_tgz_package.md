---
title: "Installing tgz package"
date: 2011-07-20
forum: General Help
---

### Post by NoFriends on 2011-07-20
Hi,

I've just downloaded a .tgz package to my desktop.

I've run tar         zxf filename.tgz

And it's extracted another folder to my desktop.

I have attempted cd into the new created directory and run the following:

./configure

./make

make install

but nothing seems to happen, I'm basically trying to install the .tgz package I downloaded

Can someone help please. ?

---

### Post by nothingspecial on 2011-07-20
Any errors?

Is there a README file?

What is the package?

---

### Post by NoFriends on 2011-07-20
Some more details:

android-sdk_r12-linux_x86.tgz


run " tar zxf android-sdk_r12-linux_x86.tgz "

created new directory with new contents.

cd into new directory

ls

add-ons directory
platforms directory
SDK
Readme.txt
tools directory

running ./configure i get ->   bash: ./configure: No such file or directory

---

### Post by nothingspecial on 2011-07-20
Output of ```
less Readme.txt
``` please

---

### Post by nothingspecial on 2011-07-20
Never mind, I downloaded it myself.

You don't need to install it. Just cd into the tools directory and run android
```

cd android-sdk-linux_x86/tools/ && ./android
```

---

### Post by NoFriends on 2011-07-20
Brilliant, Thank you for your help, From the documentation on developing android it said to download it, then install it.

Thanks.

---

### Post by NoFriends on 2011-07-20
Now i'm facing another issue, I have managed to go through all the setup stages until I do the following steps.

**Configuring the ADT Plugin**

  After you've successfully downloaded the ADT as described above, the next step is to modify your ADT preferences in Eclipse to point to the Android SDK directory:
  
[LIST=1]
[*]Select **Window** > **Preferences...** to open the Preferences         panel (Mac OS X: **Eclipse** > **Preferences**).
[*]Select **Android** from the left panel.You may see a dialog asking whether you want to send usage statistics to Google. If so, make your choice and click **Proceed**. 



When i get to this popup, It seems to freeze, does not allow me to proceed, untick or tick box, or close popup window, only allows me to minimise, unless I Force quit.

[/LIST]

---

### Post by wanttomasterlinux on 2011-07-27
hey nothingspecial
 I've read your other replies I guess you're an advance user of Ubuntu.
I'd really appreciate if you could please help me. :)
I had just installed Ubuntu (downloaded from the official website) couple of days ago. My wifi or Wlan adapter is not working. My best guess is the driver might not be installed. Apparently I found Linux compatible driver from the internet (from the xp partition) in the hope that it would work. its a .tar file. I was trying for quite a long time but couldn't install it. Tried Software Center but didn't work.
By the way, Its Dell Inspiron 6400 and my Wlan Adapter is Dell 1390 mini-PCI Wlan Card
Please help :(
Cheers

---

### Post by nothingspecial on 2011-07-27
> **wanttomasterlinux said:**
> hey nothingspecial
 I've read your other replies I guess you're an advance user of Ubuntu.


Just because I have a lot of posts don't assume I am an advanced user. I know somethings about very little, very little about some and nothing at all about most. 
> **wanttomasterlinux said:**
> 

I'd really appreciate if you could please help me. :)


No problem, although I have to go out in a minute and will not be available for some time.

> **wanttomasterlinux said:**
> 
I had just installed Ubuntu (downloaded from the official website) couple of days ago. My wifi or Wlan adapter is not working. My best guess is the driver might not be installed. Apparently I found Linux compatible driver from the internet (from the xp partition) in the hope that it would work. its a .tar file. I was trying for quite a long time but couldn't install it. Tried Software Center but didn't work.
By the way, Its Dell Inspiron 6400 and my Wlan Adapter is Dell 1390 mini-PCI Wlan Card
Please help :(
Cheers

I suggest you make a new thread in either the networking and wireless, absolute beginner or general help boards with the title

Dell 1390 mini-PCI Wlan Card

In the first post, copy and paste the output of

```
sudo lshw -C network
```

and provide a link to the tar ball you downloaded. Nobody who knows anything about this wireless card is going to expect to find a help request in a thread about installing a tgz package. I realise that is your problem, but the **actual** problem is your wireless card.

Hopefully, someone who knows what to do will see it. I promise I will have a look when I come home this evening.

Cheers.

---

