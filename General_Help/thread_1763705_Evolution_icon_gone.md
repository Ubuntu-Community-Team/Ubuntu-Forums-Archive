---
title: "Evolution icon gone"
date: 2011-05-20
forum: General Help
---

### Post by kakashi_12 on 2011-05-20
On the gnome bar (i think it's called). the evolution icon is not there. i tried to add it but cant find it. I searched for email, evolution, etc. can't find it.

---

### Post by dcstar on 2011-05-20
> **kakashi_12 said:**
> On the gnome bar (i think it's called). the evolution icon is not there. i tried to add it but cant find it. I searched for email, evolution, etc. can't find it.

It is (in) the Indicator Applet.

---

### Post by Mr. Shannon on 2011-05-20
First verify that it is installed by typing
```
sudo apt-get install evolution
```
in a terminal.

If that does't fix the problem then do the following.

For Gnome:

Is it under **Applications->Internet->Evolution Mail**?  If it is then you can drag that icon to the gnome panel.  If it's not then type
```
evolution
```
in a terminal.  If that launches evolution then you can make another application launcher with the instructions here: [http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html]("http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html") using the command **evolution**.

For Unity:

Type
```
evolution
```
in a terminal.  If that launches evolution then you can make another application launcher with the instructions given by the first comment here: [http://itshouldbeuseful.wordpress.com/2011/05/05/create-a-custom-launcher-for-unity-in-ubuntu-11-04/]("http://itshouldbeuseful.wordpress.com/2011/05/05/create-a-custom-launcher-for-unity-in-ubuntu-11-04/") using the command **evolution**.

**Hint:** now that Unity is out please say whether you are using Unity or Gnome when asking a question.

---

