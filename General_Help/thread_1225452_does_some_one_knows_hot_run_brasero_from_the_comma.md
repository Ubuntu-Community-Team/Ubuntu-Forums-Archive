---
title: "does some one knows hot run brasero from the command line in ubuntu?"
date: 2009-07-28
forum: General Help
---

### Post by roquin on 2009-07-28
does some one knows how run brasero from the command line in ubuntu? because like a lot of people im having problem making videos. thanks

---

### Post by Raffles10 on 2009-07-28
Just type:

```
brasero
```

If you're having problems you can debug and save it to a text file:

```
brasero --debug &> brasero-debug.txt
```

If you actually want to make dvd's that will play in standalone dvd players, you will need an application like [Devede]("http://www.rastersoft.com/programas/devede.html"), you would then just use Brasero to burn the resulting iso to dvd.

```
sudo apt-get install devede
```

---

### Post by tixetsal on 2009-08-05
If you are having problems with Brasero, is starting it from cmd line going to help?

I suggest typing:

man growisofs

and then follow the breadcrumbs.

I have been successful burning a couple of dual-layer discs at once, while using all manner of resources to do other fun things during the burn process, and I have never had a problem.

Good luck!

---

