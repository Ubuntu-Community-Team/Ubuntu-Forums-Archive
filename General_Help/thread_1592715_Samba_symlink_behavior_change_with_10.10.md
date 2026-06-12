---
title: "Samba symlink behavior change with 10.10"
date: 2010-10-10
forum: General Help
---

### Post by jamesisin on 2010-10-10
Ok, I have a server with my music on it.  There is a network share where all my machines can access that music.  In the past I have created a link inside the Music folder of each user/machine which links to the Samba share.  I have been doing this by linking to **/home/[username]/.gvfs/share on server**.

In 8.10 I am able to drag and drop to create the necessary link from **Music** to **share on server**.  With maybe 9.10 I lost the ability to drag and drop the link and had to resort to the command line ( ln -s "/home/[username]/.gvfs/share on server" /home/[username]/Music ).  With 10.10 I don't seem to be able to create this link using any method.  (Any link which is created is linked to / .)

(After 8.10 admin rights are required to create the link from ~/.gvfs/whatever.)

This method is very handy as all of the machines and users point to the exact same location for their music (~/Music/share) and if I can't create that link this system of organization fails.

Little help?

---

### Post by jamesisin on 2010-10-10
I must have mistyped somewhere.  Here are the necessary steps to make this work:

[LIST=1][*]Navigate to Music &#8212; **cd ~/Music**
[*]Create the link &#8212; **ln -s "/home/[username]/.gvfs/[share] on [server]" [name of link]**
[/LIST]

Replace *username*, *share*, *server*, and *name of link* as appropriate.

---

