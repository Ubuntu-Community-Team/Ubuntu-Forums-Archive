---
title: "Location of current bookmarks of firefox"
date: 2006-02-20
forum: General Help
---

### Post by Strike&gt;&gt; on 2006-02-20
Hello

I have ran into a problem that reqiures me to reinstall ubuntu, but before that i would like to save my bookmarks. but i can only do that from windows, because i can't even login to my ubuntu, so i need to know the location of the bookmarks! 

Thanx.

---

### Post by 5-HT on 2006-02-20
Hi, they'd be in:

 ~/.mozilla/firefox/<some_random_string>.default/bookmarks.html

Where <some_random_string> is just that, a random alphanumeric string that FireFox uses for your profile.


Hope that helps.

*EDIT: Sorry, didn't read this carefully. Are you asking for where windows stores your FireFox profile and bookmarks, or just where Ubuntu stores them so you can access them from windows to save the file? The path I posted is where they can be found on Ubuntu.

---

### Post by Strike&gt;&gt; on 2006-02-20
my bad, sorry

i have this program called, explore2fs, which is basically a linux explorer that will let me browse through my ubuntu partition and lets me import files from ubuntu. so that's why i want to know where it's located in ubuntu.

---

### Post by Strike&gt;&gt; on 2006-02-20
and thnx for the fast reply

---

### Post by Strike&gt;&gt; on 2006-02-20
It worked, it was there, Thank you very much!


And this pakage called gcc based was removed , so that screwed up my ubunru!;)

---

### Post by 5-HT on 2006-02-20
Glad it worked.

Did reinstalling the package not help correct any issues you were having?

---

### Post by Strike&gt;&gt; on 2006-02-20
well the problem was that many packges depended on that, important ones too, so my whole system got messed up. i lost most of my kde apps, and the next time i rebooted the pc, it would just go to the console. I tried sudo apt-get update, but it didn't even recognize that!

---

