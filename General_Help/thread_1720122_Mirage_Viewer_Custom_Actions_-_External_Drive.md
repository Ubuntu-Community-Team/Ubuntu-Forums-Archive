---
title: "Mirage Viewer Custom Actions - External Drive"
date: 2011-04-02
forum: General Help
---

### Post by Akovia on 2011-04-02
Xubuntu 10.04 (Lucid) 2.6.32-30-generic SMP i686 GNU/Linux
Xfce 4 Desktop Environment - version 4.6.1 (Xfce 4.6)
Gnome 2.30.02
Mirage 0.9.3

Hi,
I am trying to create some custom actions to copy images to predefined folders and I think it's failing due to copying from an external usb drive. Even the built-in custom action for moving a file to a favorites folder fails, so I'm hoping there is a workaround somehow.

Built in CA:
```
mkdir -p ~/mirage-favs; mv %F ~/mirage-favs; [NEXT]
```

Error:
Unable to launch "mkdir -p ~/mirage-favs; mv /media/120GB/My\ Graphics/Anime\-Manga\ Graphics/AA/Anime\ CG\ \-\ 009.jpg ~/mirage-favs; [NEXT]". Please specify a valid command from Edit > Custom Actions.

Now I know that the path has spaces, but the documentation for Mirage states **"The custom action is simply executed by the shell, so you can use pipelines and redirections as well as simple commands. Filenames with spaces or special shell characters are escaped correctly for security reasons before they're passed to the shell."** 

So I wasn't sure what to think. I figure if I can get the built-in script working, I should be fine with my custom ones. Could someone shed some light on this, or is this just not possible?

Thnx,
Ako

Update:
When I was posting this I used the CA above to copy the error, When I went back to the program I saw that the picture was gone! I also verified that the copies I made earlier to custom folders went through but I never checked because of the errors thrown. Even though I could live with clicking off the error every time (for now), is anyone familiar enough with this program to tell me how to either fix the error or surpress the dialogs?

---

### Post by Akovia on 2011-04-03
Well for anyone else that finds this, I dug up the mailing list archives for Mirage and found they fixed the bug starting in the next version. (0.9.4). Since it's not available from the deb sources, I fixed it by compiling the latest version (0.9.5)

It works like a dream now and think it's the best image "viewer" I've found so far. Extending it's functions with the Custom Actions makes it far better than Ristretto IMHO. I haven't compared them resource wise yet, but it has never locked up so far like Ristretto has. It's biggest downfall it some sort of web based support. Luckily the documentation is very good for most everything unless you hit a bug.

Hope this helps someone,
Ako

---

