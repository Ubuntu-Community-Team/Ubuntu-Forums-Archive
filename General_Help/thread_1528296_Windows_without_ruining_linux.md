---
title: "Windows without ruining linux?"
date: 2010-07-10
forum: General Help
---

### Post by HtaySigh on 2010-07-10
Hey all this is about as "general" a question as I can think of, hopefully I found the right forum. A brief overview of my problem:

~6months ago: my computer stopped successfully downloading files, I was running Vista SP2. I ignored it until:
~recently: called microsoft tech support, they failed and told me to reinstall windows. 
~yesterday: called dell after reinstalling windows didn't work (windows would not start up). they told me my hard drive was shot but I knew this was a dirty lie (I heard people joking in the background and the techie only had me restart my computer 1 time to conclude that the HD was done... seems sketchy to me). I installed Ubuntu (let it erase the whole disc) and here I am... operating my computer fully for the first time in months.

Now, I have an obligation to have windows on this computer because I need it to access my University's network. Obviously something is askew (my install disc?). I need some advice on how I can attempt to install windows on a partition of this drive WITHOUT letting it screw up linux (as I'm told it sometimes does). Also, the idiots at Dell are under the impression my hard drive is broken. They're offering to replace it for free, should I let them just so I have a new disc?

edit: just checked google, windows 7 isn't too expensive. buying that is an option if it works better. I haven't experienced that "gem"

---

### Post by drewsus on 2010-07-10
May I know what Dell computer you have? (specifically specs wise, but Im sure the model will point me in that direction).

What I could suggest as a jump off point is Micro XP in a Virtual Machine. 
You can find Micro XP from google search and I recommend VirtualBox. 

Then you can run XP inside of Ubuntu. However, there are some limitations to XP that might hamper what you want to do for school that I may be over looking, but since I dont know what exactly you are trying to achieve, I cant muse on that aspect any further. 

I have Micro XP, XP Pro and Windows 7 Ultimate running 'sexily' in VBox on an almost 10 year old computer (1.8 GHz single core - 1.5 GB RAM - Raedon x300 "As old as my grandmother" 128MB card) which I also use for a home theatre in my living room, hooked up to the TV but also sharing it all wirelessly through the house to my roommates. Its amazing what you can do with a bit of love and know-how ;)

Install VirtualBox from their repo:
```
sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian lucid non-free"
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox-3.2
```

[edit]
I might suggest having them give you that free HDD though. Its free and if there is something small wrong with yours it will only get worse.

---

### Post by mike555 on 2010-07-10
Windows 7 only runs good on newer systems and with plenty Ram ........ you can partition your harddrive and install XP , but it will mess up Grub and you will need to reinstall grub .

 have you tried Firefox with the ad-on "user agent switcher" ? sometimes that works ...

---

### Post by Serpher on 2010-07-10
Call dell again and tell them what you did. If my University demanded I had to use Windows to get on their network I'd honestly be so angry with them. What's the god damn reason for that? Microsoft payout?

---

### Post by drewsus on 2010-07-10
> **mike555 said:**
> Windows 7 only runs good on newer systems and with plenty Ram ........ you can partition your harddrive and install XP , but it will mess up Grub and you will need to reinstall grub .

 have you tried Firefox with the ad-on "user agent switcher" ? sometimes that works ...

Windows 7 actually doesnt run that bad with 512MB of RAM, but in my VM I use 768

---

### Post by Serpher on 2010-07-10
Why don't you virtualize Windows XP? Linux will simply act like a proxy.

---

### Post by Joe of loath on 2010-07-10
Why exactly do you need windows to connect to the network? You could always go ask the computer science guys how to work it, they are going to have some Linux boxes on the network.

---

### Post by drewsus on 2010-07-10
> **Serpher said:**
> Call dell again and tell them what you did. If my University demanded I had to use Windows to get on their network I'd honestly be so angry with them. What's the god damn reason for that? Microsoft payout?

I would imagine you can connect just fine with Linux and whoever set up the networks/website/whatever said that Windows is required just didn't know any better. Im studying computer science and engineering and you would be surprised just how many of my peers have very little knowledge of Linux even though our labs run on it. 

HtaySigh, have you tried connecting to your schools network with your Ubuntu computer? Can you tell me what school you are attenting/**link me to where it says Windows is required**?

---

