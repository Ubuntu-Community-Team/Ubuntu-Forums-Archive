---
title: "Help!!!!"
date: 2010-01-25
forum: General Help
---

### Post by Mashvv on 2010-01-25
Hey everybody!!! listen i need some serious help ! if would destroy my windows if anybody can help me or tell me how to convert my music from widows to ubuntu 9.4 and how to open my msn messenger without losing the contacts and not from ebuddy or something like that ! YOU WOULD BE A GREAT PERSON in my life if u help me !!
Thank You.:D

---

### Post by SuperSonic4 on 2010-01-25
If you remove windows you'll lose all data on it!

1. You don't need to convert them, ubuntu can read windows partitions so you can either mount the drive by double clicking it's icon and then copy the music or direct your favourite player to look on the windows drive. Some people also have a data partition which music is stored on (I have my music as it's own partition for example)

2. Use pidgin or empathy whichever ubuntu came with

---

### Post by feelshift on 2010-01-25
You should use more descriptive thread titles.
What do you mean by converting your music? Ubuntu can play MP3.
You can use Empathy for MSN.

---

### Post by snowpine on 2010-01-25
The 'ubuntu-restricted-extras' package installs the various codecs (mp3, flash, etc) you'll need for your multimedia collection. Open a terminal (Applications->Accessories->Terminal) and copy and paste:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

I don't know the answer to your messenger question, sorry!

---

### Post by Mashvv on 2010-01-25
Thanks guys i will try it !!! but this is a stupid question i know but  i want to delete my windows  so i want  to copy all the music files  on a USB and after deleting the windows i want to try them im afraid that they wont work because  the data will be removed from windows!?? and would i need to re add all my friends e-mails on pidgin when i open my e-mail throught it ?

---

### Post by Ordes on 2010-01-25
System and Data are two different things. Data like mp3, is not connected to the system at all. Means a mp3 song on a windows partition wont change just because you copy it on a linux partition. Systems have different applications to handle the data. But this has no affect on the data itself.....

Removing the data from windows has no affect, because you dont remove the data itself (e.g copying it on your usb)

Messengers store the contact list server-side. Not on your computer (client-side). Thats why you have to be connected to see your contacts. So no, you dont have to re-add. As soon as u connect to your msn account (e.g using pidgin), all your contacts will be there.

Pidign is no email client. It a messenger, like msn, ICQ, etc...

Email client: e.g Thunderbird, Evolution Mail (equivalent of Outlook in Win)

For email clients it is different. As email clients safe the contact on your PC, you should export all your contacts, put the data on your usb, and import them into your new email client.
Unless you are using the web-client of your e-mail account, like gmail etc.Than there is no need to import/ export

---

### Post by madmax.santana on 2010-01-25
> **Mashvv said:**
> Thanks guys i will try it !!! but this is a stupid question i know but  i want to delete my windows  so i want  to copy all the music files  on a USB and after deleting the windows i want to try them im afraid that they wont work because  the data will be removed from windows!?? and would i need to re add all my friends e-mails on pidgin when i open my e-mail throught it ?
I didn't get it..[COLOR=Red]**. Have you already deleted your Windows partition and now you want to recover the windows Documents files???**[/COLOR] Well if that is the case, I am sorry. Maybe some expert on hardcore data recovery can help you but I cannot. And in my opinion, if you delete a partition all data is irrecoverably lost.

Well if that is not the case, then I assume you still have Windows and Ubuntu on your hard disk. Or at least only Windows on your hard drive...
If you have both Ubuntu and Windows, it is not difficult at all. Just copy your music from your WindowsDrive/Documents and Settings/User-Name/My Music folder and put it in some other drive or the Music Directory in Ubuntu Home folder. Then you can delete your Windows partition and your Music files will play.
If you have only Windows and have not installed Ubuntu yet, install Ubuntu first and then do the same that I have told you above and it will be fine.
As you mentioned the USB, I think if you have large enough USB drive to hold your music, fill the Music into the USB then install Ubuntu and in the installation options you can choose to remove the Windows directory altogether. Since your Music is backed up in USB, after you install Ubuntu, you can copy the music in Ubuntu Music folder.
**Whatsoever the case, backing up your music and data is not a problem. The problem is playing it. **Ubuntu can play mp3 files but it needs codecs for that. To install all codecs, you carry out the steps proposed by **[COLOR=SeaGreen]snowpine[/COLOR]** and you are ready to go.
Anyway, if the above doesn't help you, might I ask you to [COLOR=Red]**_please re-post your question in more clear terms._**[/COLOR]

About the messenger, pidgin is marvellous. Empathy is even better, as I have heard it allows webcam and voice-chat as well. I haven't had a chance to try it yet because Empathy probably doesn't support proxy settings.** Pidgin would run MSN fine, Empathy better but only if you not behind a Proxy.**

---

### Post by madmax.santana on 2010-01-25
And by the way, NO, your question isn't stupid. It is perfectly justified, as I pondered a lot on why my mp3 files are not playing on Ubuntu, not very long ago... It's just that you have to install codecs for mp3 files and then they would run fine.

---

### Post by Mashvv on 2010-01-25
Thank u have been really helpful to me !

---

### Post by Ordes on 2010-01-25
Welcome...

Solved? 

look at my sig...

---

