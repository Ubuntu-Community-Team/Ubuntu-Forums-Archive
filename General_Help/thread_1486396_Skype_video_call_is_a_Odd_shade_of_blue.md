---
title: "Skype video call is a Odd shade of blue"
date: 2010-05-17
forum: General Help
---

### Post by BlackRat90 on 2010-05-17
ever sense i updated to 10.4 skype's video calling for me has turned a light shade of blue, nothing that really tampers with my call, just annoying the snot out of me because the person im talking to is blue.

Also I do not think its my cameras drivers because not only am I a shade of blue, but the person I am talking to is also blue and they say that I on their screen look fine. When i run a camera test with skype everything is a shade of blue as well. 

I cannot for the life of me find a way to test my camera outside of skype.

---

### Post by BrokeMahPC on 2010-05-17
To test the webcam install cheese from synaptic or the software centre. Cheese is a webcam video and picture capture program.

Are you using the latest version of Skype? Add the skype repository and key as shown below. Instead of installing, update and upgrade and it will install the latest version:
skype-ubuntu-intrepid_2.1.0.81-1
There are debs for i386 and amd64 on the skype website.
[www.skype.com]("http://www.skype.com")
[http://www.skype.com/intl/en/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en/get-skype/on-your-computer/linux/post-download/)
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

**Installing Skype**
Skype is not available in any Ubuntu software repository, and therefore cannot be installed with Ubuntu's package management software such as Synaptic or apt-get without adding a repository containing Skype. There is the official Skype repository:

You can add the Apt source like this 
```
echo "deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype" | sudo tee -a /etc/apt/sources.list > /dev/null
```Import the Apt key, even it is not used, but may be useful in future:
```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 0xd66b746e
```Install Skype:
```
sudo aptitude update && sudo aptitude install skype
```Using a repository, you will automatically receive future updates to the software. Please be aware that the repository is not signed, so when you try to install Skype, you will get a warning.

If you don't want to do that, or can't (for example, if you're on amd64), perhaps the easiest way to install is from the Debian (.deb) package available directly from the Skype website. The downside of this is that you won't automatically get future updates, you will have to download the new versions as they become available.

Debian Package
   1.Download Debian package from [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
   2. Open the file (will open with the default GDebi Package Installer).
   3. Click on install button.

---

### Post by BrokeMahPC on 2010-05-17
I also found this but use at your own risk as I have not tested it:
[http://ubuntuforums.org/showthread.php?t=1420380](http://ubuntuforums.org/showthread.php?t=1420380)
covers general blue tint on all videos - is that your problem?

---

### Post by BlackRat90 on 2010-05-18
Yes, and i believe that is the same (at least similar) graphics driver.

Rebooting my computer solved the problem, but i doubt that it completely fixed the problem.

---

