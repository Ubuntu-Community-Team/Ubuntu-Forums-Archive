---
title: "To Get FF 3.5.1.."
date: 2009-07-30
forum: General Help
---

### Post by sports fan Matt on 2009-07-30
Since Ive been away due to a broken power supply for 2 weeks ..Can someone explain how to upgrade to the mozilla version of 3.5.1? Im running 3.0.12

Thanks.

---

### Post by birdwin on 2009-07-30
I upgraded my binaries manually, but the easiest way is probably:

sudo apt-get install firefox-3.5

---

### Post by bobnutfield on 2009-07-30
> **sox fan Matt said:**
> Since Ive been away due to a broken power supply for 2 weeks ..Can someone explain how to upgrade to the mozilla version of 3.5.1? Im running 3.0.12

Thanks.

I don't believe you can update it directly from the repos for Jaunty.  But, I believe you can install it  alongside your present firefox:

[URL="http://www.psychocats.net/ubuntu/firefox"]http://www.psychocats.net
/ubuntu/firefox[/URL]

Edit: if the above works, just forget this post.

---

### Post by sports fan Matt on 2009-07-30
bash: syntax error near unexpected token `fi'
 how can you take that word out to get it alligned right?

---

### Post by birdwin on 2009-07-30
Try this:

Download the ff tarball from [http://www.mozilla.com/en-US/products/download.html?product=firefox-3.5&os=linux&lang=en-US](http://www.mozilla.com/en-US/products/download.html?product=firefox-3.5&os=linux&lang=en-US)

tar xjvf firefox-3.5.tar.bz2
sudo mv ./firefox /usr/lib/firefox-3.5
cd /usr/bin
sudo ln -s /usr/lib/firefox-3.5/firefox firefox-3.5
sudo rm -f firefox
sudo ln -s firefox-3.5 firefox

If you want to run FF 3.0, you can use 'firefox-3.0'

---

### Post by sports fan Matt on 2009-07-30
Even though its saved on my desktop..it returned this error: tar: firefox-3.5.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by birdwin on 2009-07-30
My first command assumed you're already in the same directory. Shell sessions start at the home directory, not the Desktop. Either do 

cd ~/Desktop

and then the commands, or change the first command to

tar xjvf ~/Desktop/firefox-3.5.tar.bz2

---

### Post by sports fan Matt on 2009-07-30
This is harder then I thought...Wasnt there someone I thought who wrote a beautiful install script to get the mozilla version working?

---

### Post by Arup on 2009-07-30
FF 3.51 is already in the repos, install from there and follow this guide, works wodnerfully as it sets your default browser as FF3.51 and your 3.11 is not disturbed as well. [http://ubuntuforums.org/showthread.php?t=1225754](http://ubuntuforums.org/showthread.php?t=1225754)

---

### Post by sports fan Matt on 2009-07-30
Maybe we're misunderstanding...I dont want the Shirteoko version..I am 100 percent positive that before i left 4 weeks ago, there was a very simple script of how to to get the offical version of mozilla running...I just cant seem to find the page where it was

---

### Post by lovinglinux on 2009-07-30
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by Arup on 2009-07-30
> **sox fan Matt said:**
> Maybe we're misunderstanding...I dont want the Shirteoko version..I am 100 percent positive that before i left 4 weeks ago, there was a very simple script of how to to get the offical version of mozilla running...I just cant seem to find the page where it was

[http://sourceforge.net/projects/ubuntuzilla/develop](http://sourceforge.net/projects/ubuntuzilla/develop)

Bear in mind unlike Shiriteko which works fine with all the add ons, Java and installed Flash, this x32 version installed by the script won't.

---

### Post by nanotube on 2009-07-31
> **Arup said:**
> [http://sourceforge.net/projects/ubuntuzilla/develop](http://sourceforge.net/projects/ubuntuzilla/develop)

Bear in mind unlike Shiriteko which works fine with all the add ons, Java and installed Flash, this x32 version installed by the script won't.

it will if you're running a 32bit ubuntu!

---

### Post by nanotube on 2009-07-31
> **sox fan Matt said:**
> This is harder then I thought...Wasnt there someone I thought who wrote a beautiful install script to get the mozilla version working?

yes there was :)
see [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

---

### Post by dcstar on 2009-07-31
I have just ceased using FF 3.5 - it loads pages slower than my 3.0.12, doesn't work properly with eBay and does not use the Memory Cache (I have put in a Launchpad bug).

I think I'll wait six months for a functional version to emerge.

---

### Post by sports fan Matt on 2009-08-01
Finally after a day and a half, I now have opera 10 beta and FF 3.5.1 running side by side.  The ubuntuzilla works great!

---

