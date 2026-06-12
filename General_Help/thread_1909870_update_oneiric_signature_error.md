---
title: "update oneiric signature error"
date: 2012-01-16
forum: General Help
---

### Post by HappyLinux on 2012-01-16
Even though I'm using Linux Mint, I don't think this is a Mint technical fault, thus is the reason why I'm posting here instead of in the Other OS threads.

Recently, a problem has cropped up when updates are checked from the various repos. You'll find attached an image of the error.

No doubt it's probably blocking some update checks. However, I don't know how to solve this problem. I can't figure out how to solve it seeing as it appears to be the main repo for Ubuntu.

I wouldn't be surprised if the solution is something simple.

---

### Post by Old_Grey_Wolf on 2012-01-16
Enter these commands to get the gpg key ```
gpg --keyserver keyserver.ubuntu.com --recv 5A9A06AEF9CB8DB0
gpg --export --armor 5A9A06AEF9CB8DB0 | sudo apt-key add -
```

---

### Post by HappyLinux on 2012-01-16
Bingo, problem solved. What did that do? Replace the key or something? Also, where do I go to find the key if the thing happens again?

---

### Post by Old_Grey_Wolf on 2012-01-16
> **HappyLinux said:**
> 
I wouldn't be surprised if the solution is something simple.

Funny how it turns out that way a lot of the time.

> **HappyLinux said:**
> Bingo, problem solved. What did that do? Replace the key or something? Also, where do I go to find the key if the thing happens again?

It added the GPG key to your software sources. The GPG key is used to verify that the software you are downloading is from a trusted source. You didn't have the key so the update manager didn't download the software.

The key "5A9A06AEF9CB8DB0" is in the the error you posted showing "NO_PUBKEY 5A9A06AEF9CB8DB0".

I simply inserted the key in a command I have in a file of problems and solutions that I use for helping people. The key is different for each software. ```
gpg --keyserver keyserver.ubuntu.com --recv <gpg key here>
gpg --export --armor <gpg key here> | sudo apt-key add -
```

Please mark the thread as solved. If you do not know how to do that, near the top of the webpage (scroll up) there is a menu "Thread Tools". Select "Mark this thread as solved". It lets other people searching the forums know that this had a working solution and they don't need to provide additional help.

---

### Post by HappyLinux on 2012-01-17
By any chance, could I have a copy of that file you have on problems and solutions? It might save me a lot of hassle in the future? If not, I'll continue creating my own records of such things?

---

### Post by Old_Grey_Wolf on 2012-01-17
Sorry that I prefer to keep it private. There is nothing in it that can't be found using Google. The file isn't meant to make any sense to anyone other than myself. It has instructions in it for other distros that do things differently from Ubuntu; for example, that use yum. It also has old information in it that would not apply anymore. The biggest problem with the file is that there are some instructions in it that would get me banned from the Ubuntu forum; such as, Windows Administrator password hacks, and so forth. I have to use the hacks sometime as I administer Windows computers for my children, grandchildren, aunts, uncles, nieces, nephews, and other in-laws, etc.

---

### Post by HappyLinux on 2012-01-18
I understand. I'm also a maintenance man for family computers that also run various Windows OS's, but I don't go so far as password hacks etc.

---

### Post by Old_Grey_Wolf on 2012-01-18
> **HappyLinux said:**
> I understand. I'm also a maintenance man for family computers that also run various Windows OS's, but I don't go so far as password hacks etc.

I have a 10-year old grandson that has locked my daughter out of the Admin Account on two of her Windows computers in the past few months, so yes, I have had to hack passwords. Funny thing is, that grandson may take over my job as family computer tech some day :)

When he was living with me, the first computer he had to use as his own was a Linux box I gave him. He is exploring computers and making mistakes; however, he still needs to grow in computer skills to be able to learn from those mistakes.

---

### Post by HappyLinux on 2012-01-19
My dad who is in his 60s only knows how to use office type programs, yet always asks me to install and remove something like a dozen programs a month. He has a habit of wanting to try out various programs for different tasks. The result being that his Windows machine buckles under the strange. the result being that various programs don't work right. the solution is a complete reformat and install of windows, drivers, programs etc.

My sister has a Windows laptop. Although she is fine with it she does however lend it to our brother who practically kills it by going to certain websites which end up clogging the machine with malware etc.

My older brother has a machine as well which he always asks me to repair for him.

When it comes to Linux, I'm lucky to be living on my own now. Several years ago, I had a laptop which I installed Ubuntu 8.04 on. My mum caught me playing on a puzzle game which you can't get for Windows or Mac. She asked for a go, the next thing I knew, it was difficult getting to use my laptop because she kept hogging it.

Also at one point, I even worked in a shop where you build and repair computers.

Darn in, I'm rambling on a bit.

---

