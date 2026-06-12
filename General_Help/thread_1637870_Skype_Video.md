---
title: "Skype Video"
date: 2010-12-05
forum: General Help
---

### Post by lazyshinobi on 2010-12-05
I've been using Skype for a while now, and recently, whenever I try to do a video chat, the screen that would normally show the video is transparent, showing whatever is behind it, except a bit lighter. I tried searching for similar problems, but nothing came up. I have tried to reinstall the program.

---

### Post by gjoseph on 2010-12-06
I am also having the same problem. Skype and video were working fine. I installed games from KDE Education and got trouble with skype video.
I reinstalled the skype after removing completely but the video doesn.t display. webcam works on video call and the other party can see my video. But in my display myself and the video of other person is not displayed. Test video from skype options doesn't work. it starts the camera, but doesn't display the image.

Video works fine when I test from the multimedia selector.

Suspected some video libraries used for skype is overwritten when I installed new games

Installed skype using the following commands also didn't help.

sudo apt-get install ia32-libs lib32asound2 libqt4-core libqt4-gui

All the above libs are updated.

wget -O skype_ubuntu-current_amd64.deb [http://www.skype.com/go/getskype-linux-beta-ubuntu-64](http://www.skype.com/go/getskype-linux-beta-ubuntu-64)
sudo dpkg -i skype-ubuntu-current_amd64.deb
sudo rm skype-ubuntu-current_amd64.deb


Please help with some trouble shooting steps. Its beyond my knowledge and expertise.

Moreover this is happening second time. First time happened when I added additional repositories. I had to reinstall maverick for making video work in skype after a lot of attempts.

Thanks in advance.

---

### Post by gjoseph on 2010-12-06
Hello,

I could find the following steps in the forum [http://ubuntuforums.org/showthread.php?t=1373051](http://ubuntuforums.org/showthread.php?t=1373051)

And it helped

1. make a new file from terminal

sudo gedit /usr/local/bin/skype-wrapper

2. paste the following lines in it

export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
export XLIB_SKIP_ARGB_VISUALS=1
skype &

3. change it to executable from terminal

sudo chmod 755 skype-wrapper

4. go to preferences > main menu > internet > skype and click properties and in the command textbox type

/usr/local/bin/skype-wrapper

Regards

---

### Post by vangop on 2010-12-11
Skype is already started via skype-wrapper (/usr/bin/skype-wrapper)
I had several issues with skype video, collected the fixes [http://ubuntu-answers.blogspot.com/2010/10/skype-issues-on-ubuntu.html]("http://ubuntu-answers.blogspot.com/2010/10/skype-issues-on-ubuntu.html")

---

### Post by attam on 2011-02-05
I had a similar problem with my skype in ubuntu (in my case, the person I was talking to could see me, but I could not see them).
Don't understand how it works, but the new skype-wrapper trick described above solved the problem.
Thanks.

---

