---
title: "video calls"
date: 2009-09-08
forum: General Help
---

### Post by hemajith on 2009-09-08
I used Ubuntu for a while and I really liked it. But I had to switch back to Windows as I am using lot of video calling through msn and amsn in Ubuntu was giving me problems. 

What I want to know is, has things improved in the latest version of kubuntu? I'm using a USRobotics 9640 webcam. Will that be compatible? the driver cd does not contain any Linux drivers. Anyone has any experience in video calling with msn clients?

Thanx...

---

### Post by Claus7 on 2009-09-22
Hello,

I think that when karmic is out, then many improvements in this section are awaited.

Regards!

---

### Post by 3rdalbum on 2009-09-22
There is currently no video calling (voice and video) support over MSN, using the actual MSN protocol. However, I use Meebo as my instant messaging client; it can connect to MSN and uses Tokbox to provide voice-and-video functionality to the ordinary IM networks. Try it; it works.

Otherwise your friends could install Skype, which has voice and video over the Skype network on Windows, Macintosh and Linux.

---

### Post by P4man on 2009-09-22
No experience, but find out :). You can even try amsn on windows and see if you like it, or just download the latest (k)ubuntu, put it on a usb stick, install asmn and give it a spin.

---

### Post by hemajith on 2009-09-22
I would dearly like to go back to Ubuntu/Kubuntu. The worry I have is that I have only one PC (laptop) and I cant have it on dual boot since I have limited disc capacity. Have a lot of data too. So I need to find out whether my USRobotics 9640 USB webcam will work with Ubuntu/Kubuntu

---

### Post by rajeev1204 on 2009-09-22
> **hemajith said:**
> I would dearly like to go back to Ubuntu/Kubuntu. The worry I have is that I have only one PC (laptop) and I cant have it on dual boot since I have limited disc capacity. Have a lot of data too. So I need to find out whether my USRobotics 9640 USB webcam will work with Ubuntu/Kubuntu

WHats the output of lsusb in a terminal?

Also, try cheese to test the webcam

sudo apt-get install cheese

Menu>accessories>cheese.

---

### Post by hemajith on 2009-09-25
> **rajeev1204 said:**
> WHats the output of lsusb in a terminal?

Also, try cheese to test the webcam

sudo apt-get install cheese

Menu>accessories>cheese.

I tried the video cam with a Kubuntu 8.10 live cd and the the usb listing I got was,

0c45:6242 Microdia PC Camera (SN9C201)

what do you make of that?

Thanx

---

### Post by |{urse on 2009-09-25
Amsn is a full featured chat client that does support webcams using the msn protocol. 
 
sudo apt-get install amsn
 
-or-
 
grab the latest version here
 
[http://www.amsn-project.net/](http://www.amsn-project.net/)
 
I've been using it for years now.

---

