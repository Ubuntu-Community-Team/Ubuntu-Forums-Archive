---
title: "Can't Install anything"
date: 2011-04-03
forum: General Help
---

### Post by chand.sethi77 on 2011-04-03
[SIZE=4]I am using Ubuntu 10.04. I am new to it still I got some basic knowledge of terminal and ubuntu software center. I installed a few programs but after a few days, before I download something, the following error occurs:
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
I did apt-get install -f still it give an error.
Another problem is when I download something like .tar.gz (some extension like this) The page keeps on loading and nothing happens. 

THE MAIN PROBLEM:: I installed apache , mysql and php from terminal as given by a website. I want to unistall it and install LAMPP or XAMPP. Please tell me how to do that. When I click on link to download XAMPP, the page only keeps loading and nothing happens. I'm sure this is not fault of my Internet service Provider. 
THANKS!:KS
[/SIZE]

---

### Post by 3Miro on 2011-04-03
LAMP howto:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If you are new to Ubuntu, avoid installing things from the terminal. Try using Synaptic Package Manager (System -> Admin -> Synaptic). SPM will guard you from mistakes.

When you get an error, then make sure to copy and paste that here using code tags (see the little menu on the top of where you write your post, you can select Quote, Code and other options). Without seeing the exact error that you get, we cannot guess how to help you.

I am not sure I understand the problem with the web-page. Can you please be more organizes like this:

1. I have a problem with .... When I do this .... then this happens ....

2. Another problem that I have is ......

---

### Post by chand.sethi77 on 2011-04-04
# 1.  I have a problem using INTERNET in Ubuntu 10.4 .. It happens to some particular sites. When I open Login page of Yahoo or Hotmail it just shows that it is loading.... nothing else.

---

### Post by 3Miro on 2011-04-04
> **chand.sethi77 said:**
> # 1.  I have a problem using INTERNET in Ubuntu 10.4 .. It happens to some particular sites. When I open Login page of Yahoo or Hotmail it just shows that it is loading.... nothing else.

Are you using Firefox? Check the settings for Cookies and Flash Block, Ad Block and No Script. Those can interfere with Yahoo and Hotmail. My money is on the Cookie settings. You should also enable JavaScript.

---

### Post by Dark Dreamer UK on 2011-04-07
If you're still have problems install try this.

sudo apt-get upgrade

you may get a message to install something
press n (as it probably a package causing the problem)

then try.

sudo apt-get install -f

---

