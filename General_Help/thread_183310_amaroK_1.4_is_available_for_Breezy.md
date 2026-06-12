---
title: "amaroK 1.4 is available for Breezy"
date: 2006-05-27
forum: General Help
---

### Post by adamkane on 2006-05-27
Reference:
[http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10]("http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10")

Still using amaroK 1.3 with breezy?

```

sudo gedit /etc/apt/sources.list

``` 
Add this line to the file:

> 
deb [http://archive.czessi.net/ubuntu]("http://archive.czessi.net/ubuntu") breezy main universe
 

Save and close the file. Continue:

```

cd ~/Desktop
wget http://www.czessi.net/kczessi.gpg
sudo apt-key add kczessi.gpg
sudo apt-get update 

``` 

If amarok is already installed:

```

sudo apt-get dist-upgrade

``` 
  
If amarok isn't already installed:

```

sudo apt-get dist-upgrade[FONT=monospace]
[/FONT]sudo apt-get install amarok amarok-xine

``` 

Be aware that amarok-gstreamer is not available for amarok 1.4. You will be using amarok-xine.

---

### Post by PriceChild on 2006-05-27
Your code didn't work for me, but just added that repo to my list and am doing a quick upgrade right now.

Pricey

-UPDATE-

Installed fine, uncommented out the repo now just incase.

I love Amarok... i like rhythmbox for its simplicity... but sometimes you need features such as being able to get it to rearrange your music library into decent folders :)

---

### Post by mcdoogle on 2006-06-03
Thankyou, thankyou, thankyou!

I have been trying to install the latest version for the last 30 mins, muchos gracias.  All steps work fine for me!

---

### Post by adamkane on 2006-06-05
Yes, all steps should work now. The kubuntu people obviously didn't test before they posted the steps to get amaroK 1.4 working on breezy.

---

