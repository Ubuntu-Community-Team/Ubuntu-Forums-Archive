---
title: "How do i use adduser?"
date: 2009-09-12
forum: General Help
---

### Post by weryl on 2009-09-12
Hi,

I've just installed Planeshift and the folder's owned by root:games. In order to play I figured I had to add my username to the group "games" so I typed:

sudo adduser username games

Which exits normally. However if I type "groups" afterwards I get a list of groups without "games" in it. If I try to run adduser again it tells me that "username" is already a member of "games", and I still get a "permission denied" when I try to run the game from the menu.

Am I doing something wrong? If the console tells me that "username" is already a member of "games" why can't I run the game? And why doesn't it show up in the list of groups I belong to? Also is the "Users and groups" window in the System tab suppose to work? I don't even show up as a member of my own group in there (say mike isn't a member of mike, which i kinda am)...

---

### Post by harrismh777 on 2009-09-12
hi Mike,
There is more to it than ower and group... you also have to consider permissions. Other users on the system may or may not have execute authority on the code within the folder. 

-rwxr-xr-x   root games     whatever

In the above example root (the owner) has read, write, execute... games (the group) has read, no write, and execute, and other has read, no write, AND execute.  Everyone on the system who has access to the folder will be able to execute this program even if they are not in group games.

-rwxr-xr--   root games     whatever

In the above example OTHER has no execute permissions and will not be able to run whatever, unless they are a member of group games. 

If you have correctly installed the game it is unlikely that you will have to manually set permissions...  strange.

Did you install as root?  Did you use Applications-->Add/Remove ?  or did you install a package manually (as root?)

---

### Post by weryl on 2009-09-13
Hum I just needed to logout... sorry about that.

By the way PlaneShift is so lame, just ridiculous. Don't try it.

---

### Post by ineedacold1 on 2009-10-07
Hello,
Is there a way to have the adduser and deluser take effect without rebooting?

I have a script that I add myself to 'muzak' group to change tags on my music, then i remove myself from the group so that I do not mess the tags up.

I have dr-xrwxr-x permission on the folder and the group is muzak, owner is me

---

