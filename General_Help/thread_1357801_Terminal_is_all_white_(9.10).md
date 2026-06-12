---
title: "Terminal is all white (9.10)"
date: 2009-12-17
forum: General Help
---

### Post by Hydrofarmer on 2009-12-17
Why is my terminal white? And whats the command to reformat your HDD?

---

### Post by TyrantWave on 2009-12-17
In the terminal, type reset and press enter. Should put it back.
Either that or the theme of it's been changed, so go Edit -> Profile Preferences -> Colours.

To reformat the HDD? As in completely wipe it?
Well, easiest way to do that is boot into a Live CD, and format the partition as a whole from GDisk Partitioner.

The fun way to do it is "rm -rf /", although I severely advise **against** using that! It's not an actual format, it just deletes everything in the filesystem

---

### Post by hwttdz on 2009-12-17
"Thats like asking how can an ant carry 100 times its body weight and ice cream still be delicious? Are the two even related?"

But your terminal is white because that's the default, it you want to change it "edit"->"profile preferences"->"colors"->uncheck use system colors and choose a scheme of your choice

And for the second, gparted can do almost any sort of file system operation, you might have to be more specific about what you mean by reformat otherwise.  Do you want to reformat as ext4? or ntfs? do you want to erase the data but leave the partition intact?

---

### Post by lewisforlife on 2009-12-17
> Why is my terminal white?

That is the default color of gnome-terminal.

---

### Post by s.fox on 2009-12-17
Hi

[This]("http://ubuntuforums.org/showthread.php?t=267869") may be of some use to you.  Be careful with that tutorial.

-Silver Fox

---

### Post by Julita on 2009-12-17
See, nothing is permanent :) Are you complaining about white style? For HDD (e.g., external) GParted is the right thing to use.

---

### Post by supermelon928 on 2009-12-17
White's the default, I recommend changing it to black for optimum nerd productivity.

---

