---
title: "Need a Video DVD Burning Program"
date: 2010-07-07
forum: General Help
---

### Post by JustSomeGuy805 on 2010-07-07
I'm having a hell of a time looking for a program that will burn a video DVD file structure stored on my hard disk.  I already have all the DVD files in the VIDEO_TS folder copied to my hard drive.  I just need a burning program that will burn those files to a DVD and make a DVD that will actually play in a DVD burner.  

I tried using Brasero to just burn a data DVD with the files from my hard drive but that didn't work as the DVD didn't play.  DeVeDe it seems is for transcoding other files into DVD files.  I have to manually add all the vob files individually and the menus aren't preserved... that's too much trouble for my end users.  No option in GnomeBaker...

Can anyone recommend me a simple program for this simple task?

---

### Post by claracc on 2010-07-07
You can try with k3b. It is in the repositories, so you can install with synaptic.

If your desktop is gnome, it will install some needed kde libraries, but it works very well.

---

### Post by JustSomeGuy805 on 2010-07-07
hey thanks for the response.  Will installing k3b "bloat" up my system since I am using a gnome desktop and it will have to install the kde libraries?

---

### Post by philinux on 2010-07-07
> **JustSomeGuy805 said:**
> hey thanks for the response.  Will installing k3b "bloat" up my system since I am using a gnome desktop and it will have to install the kde libraries?

I seem to remember when I installed k3b it downloaded about 90meg. This would expand by about 3 times I think.

However it is a very good app. If you dont like it remove it then use apt-get autoremove.

I'm surprised gnomebaker has no option. I would double check the help pages.

---

### Post by Linuxforall on 2010-07-07
Have you tried DeVeDe, its in the repos, uses mencoder and works quite well.

---

### Post by kpkeerthi on 2010-07-07
Here is a command line way to create an ISO:

cd to the directory containing the vob files (you will see a directory named VIDEO_TS) and run mkisofs from this location :

```

mkisofs -v -dvd-video -o ../my_movie.iso .

```

And then use your favorite burner program to burn the ISO on a DVD.

---

### Post by JustSomeGuy805 on 2010-07-07
> **Linuxforall said:**
> Have you tried DeVeDe, its in the repos, uses mencoder and works quite well.
Yes, see first post.

> **kpkeerthi said:**
> Here is a command line way to create an ISO:

cd to the directory containing the vob files (you will see a directory  named VIDEO_TS) and run mkisofs from this location :

```

mkisofs -v -dvd-video -o ../my_movie.iso .

```And then use your favorite burner program to burn the ISO on a  DVD.

Thanks for the suggestion. It says missing pathspec.  However, thinking about it, I  don't think that method is very practical for my end-users.

---

### Post by kpkeerthi on 2010-07-07
You probably missed the trailing . (dot)

---

### Post by JustSomeGuy805 on 2010-07-07
> **kpkeerthi said:**
> You probably missed the trailing . (dot)
psychic...

---

### Post by philinux on 2010-07-07
With k3b. Click the More Actions button. Choose New Video DVD etc. Or From File >new project> New video DVD

Add files off you go.

---

### Post by JustSomeGuy805 on 2010-07-07
> **philinux said:**
> With k3b. Click the More Actions button. Choose New Video DVD etc. Or From File >new project> New video DVD

Add files off you go.

I was hoping not to have to install the kde libraries as the computer is rather old, but everyone seems to swear by k3b.  I'm going to tinker with automating kpkeerthi's method through like a script of somethin for right now and maybe try k3b later.

---

