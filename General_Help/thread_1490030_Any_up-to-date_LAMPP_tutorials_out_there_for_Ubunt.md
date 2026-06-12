---
title: "Any up-to-date LAMPP tutorials out there for Ubuntu 10.04?"
date: 2010-05-21
forum: General Help
---

### Post by CoolBreeze47 on 2010-05-21
Hi everyone :)

Can anyone here point me to a complete, up-to-date, user-friendly, step-by-step LAMPP tutorial for Ubuntu 10.04?. I've been running Linux for a long time and I've run may different WAMPP servers but I've never run a Linux server and I'd love to try it!.

There is a tutorial out there for a much older version of Ubuntu but it is very out-of-date. The one I saw contained exact step-by-step instructions for what needed to be done and in precise order. It's a shame it was outdated but if anyone can point me to a new/modern version I'd really appreciate it.

Thanks so much!.

- Regards, CB

---

### Post by wojox on 2010-05-21
Have you looked at [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html")

---

### Post by CoolBreeze47 on 2010-05-21
Wow, that was quick...thanks!.

Thanks for the link. That was very nice but actually, I'm looking for one with much less detail and more 'straight to the point" rather than a comprehensive guide. The one I was looking at (which is outdated) was a single-page tutorial and provided about 15 step-by-step terminal commands to set up a complete server on Ubuntu. It was very popular and got really good reviews by people who used it.

Is there anything like that out there?.

Thanks again, CB

---

### Post by bodhi.zazen on 2010-05-21
```
sudo apt-get install apache2 php5 mysql-server
```

---

### Post by Nythain on 2010-05-21
howtoforge's "perfect server" guides are pretty good, ignoring the stuffs you don't really care about, like ispconfig and the mail stuff

---

### Post by CoolBreeze47 on 2010-05-21
> **Nythain said:**
> howtoforge's "perfect server" guides are pretty good, ignoring the stuffs you don't really care about, like ispconfig and the mail stuff

Yes, I think that was the site where I saw the outdated tutorial. It was excellent and went beyond a few terminal commands. It showed how to quickly and easily configure your new server too and how to install/configure phpmyadmin, etc. I think there was a comment thread there too but as the information became more and more outdated, people were getting confused and having issues getting everything set up, thus, I'm looking for something very similar but more up-to-date. Any links would be greatly appreciated :)

- CB

---

### Post by Nythain on 2010-05-21
google "howtoforge perfect server 10.04" you'll get a moar up to date guide :) at least if you're running 10.04

---

### Post by akakingess on 2010-05-21
> **bodhi.zazen said:**
> ```
sudo apt-get install apache2 php5 mysql-server
```

+1, that's about it, that will install Apache, PHP, and MySQL, and then you are done. Go to Localhost within your browser to confirm, but that is it. Then, if you want to go into more detail you could just look that up in the more detailed tutorials as needed.

---

### Post by CoolBreeze47 on 2010-05-21
Thanks all. Just bookmarked this thread and the tutorial on How To Forge. I was thinking that was the "outdated" one but it looks like one I've never seen before and after reading through it, it looks very good. I'll either keep it simple and use the method bodhi.zazen and akakingess suggested or maybe use the guide on How To Forge (maybe both). Anyway...

Thanks again, CB

---

### Post by orlox on 2010-05-21
> **bodhi.zazen said:**
> ```
sudo apt-get install apache2 php5 mysql-server
```

Arent you missing mysql module for php?

```

sudo apt-get install apache2 php5 mysql-server php5-mysql

```

---

### Post by bodhi.zazen on 2010-05-21
> **orlox said:**
> Arent you missing mysql module for php?

```

sudo apt-get install apache2 php5 mysql-server php5-mysql

```

Well, you could add several php modules ... but yes probably a good idea to add that and a few others, it depends on what you are wanting to do, and the OP seemed to be asking for the readers digest version of how to install LAMP =)

---

### Post by CoolBreeze47 on 2010-05-21
> **bodhi.zazen said:**
> and the OP seemed to be asking for the readers digest version of how to install LAMP =)

What I was looking for was just a simple tutorial - similar to an outdated one I had seen with easy-to-follow and step-by-step instructions. I can easily install anything I need (you only need apt for that). It's getting everything configured to work properly that is of concern here. Not sure what you meant by "Reader's Digest version"...

- CB

---

### Post by robvas on 2010-05-21
Start by installing the packages just mentioned. Then try to run a php script from your web browser. If it doesn't work, figure out why, most of the time you just have to add another package (or two) or change a setting.

Keep track of all the commands you have used so far. When it works, you now have the complete guide to setting up LAMP on Ubuntu!

Come back and share it with us.

Each different thing you install on your server (forum, image gallery, CMS) is going to want other libs (zlib, gd, etc), so you'll have to refer to a step-by-step guide for those as well.

---

