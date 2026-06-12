---
title: "Compiz Help"
date: 2006-03-07
forum: General Help
---

### Post by clemcat on 2006-03-07
I am trying to install compiz/xgl on my system, and I have hit a snag.  I am following the directions from here:

[http://www.ubuntuforums.org/showthread.php?t=131267&highlight=compiz](http://www.ubuntuforums.org/showthread.php?t=131267&highlight=compiz)

when I type in :

sudo apt-get install compiz xserver.............compiz-gnome

I get an errot that reads:

Reading package lists........done
Building dependancy tree......done
E: Couldn't find package compiz

I have all repos (multi/universe) enabled, did I miss something?:-k 

Thanks,

Chris

---

### Post by o_fortuna on 2006-03-07
[QUOTE=clemcat]I am trying to install compiz/xgl on my system, and I have hit a snag.  I am following the directions from here:

[http://www.ubuntuforums.org/showthread.php?t=131267&highlight=compiz](http://www.ubuntuforums.org/showthread.php?t=131267&highlight=compiz)

when I type in :

sudo apt-get install compiz xserver.............compiz-gnome

I get an errot that reads:

Reading package lists........done
Building dependancy tree......done
E: Couldn't find package compiz

I have all repos (multi/universe) enabled, did I miss something?:-k 

Thanks,

Chris[/QUOTE]
Are you running the Breezy Badger (5.10)? If so, there's no hope, as Breezy's libraries are to old to support Xgl/Compiz anyway, and the packages for Xgl and Compiz are not included, and will not be included, in the Breezy repos. The thread you linked to discusses the installation of Xgl and Compiz under Dapper, for which packages have been built.

So, the moral of the story is: If you want to run bleeding edge stuff, you gotta run the bleeding edge distribution. Dapper is pretty stable right now, and I use Xgl and Compiz with it. If you can't wait 'till April to try Compiz, just find the .iso files for Flight 4 and download away!

---

### Post by clemcat on 2006-03-07
DOH!, see what not reading directions does!  Well, I m going home after class and loading Dapper up onto the machine.  

Does anyone know how Dapper 64 bit runs, I have Dapper 32-bit and it seems fine, will I gain anything from using/not using the 64 bit edition of Dapper?

Thanks for any guidance.

Chris

---

### Post by magnusbb on 2006-03-08
[QUOTE=o_fortuna]Are you running the Breezy Badger (5.10)? If so, there's no hope, as Breezy's libraries are to old to support Xgl/Compiz anyway, and the packages for Xgl and Compiz are not included, and will not be included, in the Breezy repos. The thread you linked to discusses the installation of Xgl and Compiz under Dapper, for which packages have been built.

So, the moral of the story is: If you want to run bleeding edge stuff, you gotta run the bleeding edge distribution. Dapper is pretty stable right now, and I use Xgl and Compiz with it. If you can't wait 'till April to try Compiz, just find the .iso files for Flight 4 and download away![/QUOTE]

Not in my experience. I am running XGL / Compiz (not the newest version, though, but the one Novell released last month) with Breezy, and it works great! I haven't modified anything, except that I converted a couple of RPMs to the DEB format and installed them with this excellent guide:

[http://www.ubuntuforums.org/showthread.php?t=133772&highlight=breezy+xgl](http://www.ubuntuforums.org/showthread.php?t=133772&highlight=breezy+xgl)

For those who don't want to ruin their good Ubuntu desktop experience now, by upgrading to an utmost unstable distribution, please consider trying this guide. 

Further, since XGL doesn't work great with everything yet, I have made a script (took it from another excellent guide in this forum) which gives you the choice at GDM startup; normal X.org or the XGL one.

---

