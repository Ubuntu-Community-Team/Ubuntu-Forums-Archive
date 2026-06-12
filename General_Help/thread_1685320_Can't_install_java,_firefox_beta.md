---
title: "Can't install java, firefox beta"
date: 2011-02-10
forum: General Help
---

### Post by ThaDoctor99 on 2011-02-10
Hi 
I got this amazing new version of firefox which is really nice.
Well the only problem is that I can't get firefox to recognize java.
Can somebody help me ?

---

### Post by drewsus on 2011-02-10
How did you install java? 
How did you install this "amazing new version of firefox"? 
What version is it? 
Did your old version work fine? 
What is your old version. 
What version of Ubuntu are you using? 
People really need to be as verbose as possible when asking for help. We aren't magicians/psychics and there are SOOO many different ways to do things which result in entirely different solutions!

---

### Post by ThaDoctor99 on 2011-02-11
First of it worked fine with the firefox 3.6 I had before
In my ubuntu 10.10
Now I got the firefox 4 beta 10
I got the icedtea java plugin which worked rather nice with the other version of firefox 

I installed the firefox beta by downloading the package from mozilla and then copying that to my path (/usr/bin/firefox) also all the other stuff from that package.

---

### Post by drewsus on 2011-02-11
Okay, we are going to install Sun Java Runtime Environment. Bouyah! 

Before proceeding, close all instances of Firefox.

1) First we need to enable the Partner repository. If you know you have already done this previously, you can skip this step.

```
sudo add-apt-repository "deb http://archive.canonical.com/ maverick partner"
```

2) Resynchronize the package index.

```
sudo apt-get update
```

3) Install Sun Java: 

```
sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
```

4) Set Sun Java as default:

```
sudo update-java-alternatives -s java-6-sun
```

That should be it. Start Firefox and lets see where you are.

---

### Post by ThaDoctor99 on 2011-02-11
Well That did not work.
I have this feeling that firefox just really don't like java.
when I do a 
about : plugins 
it shows me that I got flash and nothing else.

---

### Post by drewsus on 2011-02-11
Well I know that java works for me in both 3.6 and 4.0. Hmmm

---

### Post by ThaDoctor99 on 2011-02-11
Yeah but mine won't work.
Well I can't think of a reason for why not.
Perhaps I should try the older version of firefox.

---

