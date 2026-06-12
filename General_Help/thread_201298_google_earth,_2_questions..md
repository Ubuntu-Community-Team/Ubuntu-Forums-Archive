---
title: "google earth, 2 questions."
date: 2006-06-21
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-06-21
When google earth opens up, there is no screen for where the globe should be, it's just black.

Also, can you put google earth in applications -> Internet?

any help would be much appreciated

---

### Post by s_h_a_d_o_w_s on 2006-06-21
Nevermind about 2nd question, I got it with alacarte

---

### Post by bruce89 on 2006-06-21
[QUOTE=s_h_a_d_o_w_s]Also, can you put google earth in applications -> Internet?[/QUOTE]
It should be there anyway.

---

### Post by grendelkhan on 2006-06-21
It doesn't make an entry.  Known bug I believe.

---

### Post by Fred Doolie on 2006-06-21
[QUOTE=grendelkhan]It doesn't make an entry.  Known bug I believe.[/QUOTE]

It does on my system. 
-------------------------------------------------------------------
To get rid of the black empty screen go to any location. Sometimes I get the black screen and sometimes I get black patches in a good screen. The Win version does this too. I think it's because that particular piece of the map didn't download. GE gets all it's data on the fly from your net connection you know.

---

### Post by s_h_a_d_o_w_s on 2006-06-21
It shows up, but won't start. What command did you put for yours? sudo googleearth?

---

### Post by grendelkhan on 2006-06-21
Get the fudge out.

I had to add an entry manually, but I haven't restarted gnome-panel since I installed it, so it may be there and just lurking.

---

### Post by Jasper Houtman on 2006-06-21
That's because you installed as root.
Use sudo chown -D user:user directory/directory to switch ownership of the shared directories back to you.
After that the Googleearth icon will show up in your menu.
It's a known bug in the install which will be fixed in later releases

For an easy fix. reinstall in your home directory as a normal user. (Without the sudo command).

If your screen is black then maximize your window and then set it back to normal.
I have to do this everytime I start up google earth (also known bug, will be fixed in later releases).

---

### Post by JoWilly on 2006-06-21
If you installed as root/sudo , just copy/link /opt/google-earth/googleearth.desktop to /usr/share/applications to get the icon in the internet menu.

(replace opt with the place you installed it).

---

