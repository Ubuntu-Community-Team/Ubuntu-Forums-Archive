---
title: "Media Streaming Center"
date: 2010-08-20
forum: General Help
---

### Post by jsmkbunch2000 on 2010-08-20
Alright, I have spent several days trying to figure out a good Media Streaming Center.   What I want to do is basically use my laptop in my room with a browser (ie Firefox) go to my media center where I keep all my movies, music and photo's - I USE XMBC currently - and would like to actually just click on a movie or music album and access it through my broswer over my wifi connection.  I have used VLC, but you have to start a move or song from the computer already to be streaming and can't "broswe" around for a particular movie without already streaming THAT movie to begin with.  What I'd like is like the XMBC browser GUI that you can access the "controls" to start movies, it there something that looks like this that would stream then to the computer you were currently on after browsing through your media in another room and then start a stream based on your selection?  I use Ubuntu Desktop 10.04 on my laptop and currently run the XMBC in my livingroom on a Windows XP machine.  I can change it over to Linux, but was trying it out first.  Does anyone have a way to :share" their media through streaming with the full menu options so you can simply choose what you want to watch after browsing it all from another room through a browser like firefox, ( or even if I wanted to remotely access the media center via the internet when on trips using http or https)?

I should mention, I am not wanting to VNC first to start a movie stream, I'd like to just have full menu options like I do on the local machine but have EVERYHTING streamed to my browser on a different computer on my network as an option.  Is this at all possible?

---

### Post by lovinglinux on 2010-08-20
You can simply setup a shared folder using SSHFS or something else, then open the file from the remote folder using your local player. 

You don't need to stream the video, unless you want for example to capture TV on the Media Center and stream it live to another machine .

See [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

Make sure you configure the ssh server on the Media Center machine using key authentication.

See:

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

If you don't have a router, you might also want to block access to port 22 form outside your lan, so you can only access the ssh from your local network.

---

### Post by jsmkbunch2000 on 2010-11-04
Actually, what I'd like to do is to be able to do something like what Netflix has. Where you can go to a page, select a move, and it will play it in a browser window.  I'd also like to be able to access it from anywhere with a high speed connection when I am away from home from a laptop or something that is on my home network without having to download it or share it as file. When I go to my Netflix "Watch Now" movies, they start right up and you can even fast forward, pause, or choose another movie.  Is there anything that I can set up to make my own home movie media center that can do this?   Or anther example is like hulu.com.  Is there something that can do this for personal use?  And that might even be able to allow different users to "login in" and watch an entirely different movie of their own selection at the same time???

---

### Post by thatguruguy on 2010-11-05
You could put mythbuntu on your media center at home, and then use xbmc on your laptop to view the movies on your media center.  I have both xbmc and mythtv frontend on my laptop.  Plus, you can also stream live tv to your laptop that way when you're on your network.

Mythbuntu has a way to stream media files over the internet (known as "mythweb"), but I haven't tried it for streaming yet.  Essentially, it serves the videos up as flash files.  You can get an overview of mythweb [here]("http://www.mythtv.org/detail/mythweb").

---

