---
title: "Thunderbird just went from bad to useless"
date: 2012-02-24
forum: General Help
---

### Post by Windoze Refugee on 2012-02-24
OK 
So I've been using TBird for a few months now but try as I might I cant get  it to co-operate with my mail server. I have my own website which has a  mail server component. I set all the settings in TBird but the only way I  can get it to work is to open a webmail version of one of the mail  accounts. 
Once that's up and running, TB will beaver away downloading and  uploading all the mail for that account, and all the others set up on  my version of TB even though only the primary account is open on the  webmail. 

I've done this workaround for months but yesterday I did a system update, and ever since TB wont connect to my mail servers AT ALL no matter what I do.
So I thought Id try and upgrade from my pitiful and clunky 3.1 (something) version to the shiny new TB 10.0.2... but of course it wont upgrade on its own, will it?...
So I try the sudo command ( sudo add-apt-repository ppa:mozillateam/thunderbird-stable) to install the update doo dah. And again.
And again...and again...and again...and again....etc etc etc... 

And the eventaul (after 15 mins) response EVERY time is Cannot connect to server!!!!

ARRRGHHHHH!!!!

Can ANYONE tell me what Im doing wrong? 
Please.  
This is all getting on my very last nerve.
All help gratefully received.  
Cheers 
Jonathan

---

### Post by Windoze Refugee on 2012-02-24
Oops - soz folks, just seen I'm prolly in the wrong place with this post. Mods? Little Help?
Ta muchly

---

### Post by Paddy Landau on 2012-02-25
Sometimes the servers are offline, and all we can do is wait a few hours or even a full day.

However, let's check that your server is correctly set. Open Software Sources > Other Software. Your Thunderbird line should read:
```
http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu oneiric
```(Substitute *oneiric* for your distro if you aren't using 11.10.)

---

### Post by Windoze Refugee on 2012-02-25
HI Paddy. Many thanks for your input. Ive actually now managed to solve the problem. It was, as you say, to do with the servers being busy I think. Mods you can mark this solved. Many thanks. Jonathan

---

### Post by Paddy Landau on 2012-02-25
Cool, I'm glad that's solved.

> **Windoze Refugee said:**
> Mods you can mark this solved.
You [do it yourself]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") on these forums.

---

