---
title: "Admin login"
date: 2011-02-14
forum: General Help
---

### Post by alpetjr on 2011-02-14
I am a new user using Kubuntu. So far I really like it, but I have a problem. I went to the Software Center/Edit/Software Sources.I was asked for my Administrative Password. I typed in my password and pressed "OK" and got a message saying that my password is incorrect.I get asked for my password all the time (don't really bother me) but why would it reject it when I am trying to add a repository? Anyone have any ideas? Thanks

---

### Post by kn0w-b1nary on 2011-02-14
i don't know the answer but here is a possible fix:

restart computer, and just after BIOS screen hit shift, you have to be fast,and it might take you several trys. then select recovery mode, then drop to root prompt.
type "passwd" to change root password. then type "visudo" to make sure that you're on the sudoer's list.

Hope this helps!

---

### Post by ajgreeny on 2011-02-14
> **kn0w-b1nary said:**
> i don't know the answer but here is a possible fix:

restart computer, and just after BIOS screen hit shift, you have to be fast,and it might take you several trys. then select recovery mode, then drop to root prompt.
type "passwd" to change root password. then type "visudo" to make sure that you're on the sudoer's list.

Hope this helps!
A root account and password is not needed or recommended in ubuntu or any of the *ubuntu family of OSs.  Are you certain the the password you typed was correct, and that you did not get upper case muddled or something similar?

What about logging in at the start of the session; does your password work OK then or do you have the system login automatically?

You can reset **your** password using recovery mode, but **do not** set a root password as it may mean a lot of information here on the forum and in other reference sites will not work for you, and may be very confusing later on.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by kn0w-b1nary on 2011-02-14
@ajgreeny
It's good security policy, but you're right.

---

### Post by Iowan on 2011-02-14
I suppose you wouldn't be lucky enough to have it be something simple like CAPS LOCK?

---

### Post by alpetjr on 2011-02-15
I logged in at startup fine. I tried to put my password in for software sources and I get told that my password is wrong again.

---

### Post by alpetjr on 2011-02-15
I went into software sources downloaded and installed a program just fine. Is the administrative password different than my normal password?

---

### Post by mastablasta on 2011-02-15
as it was advised try changing your password. somehting is wrong. likely you are really typing it in wrong or have some key on like caps lock.

---

### Post by alpetjr on 2011-02-15
I did what you said. I still have my regular login password. Now I can login Admin in the Software Center. Thanks. Where can I go to bypass the start up login? I found it one time before but I cannot remember where it is.

---

### Post by kn0w-b1nary on 2011-02-15
there is a program called "Login Screen". from there you can set it to auto-login.

EDIT: Oops.. I forgot this was Kubuntu. I'll look though as i used to use KDE.

---

### Post by alpetjr on 2011-02-16
Found it

---

### Post by kn0w-b1nary on 2011-02-16
> **alpetjr said:**
> Found it

Great, enjoy KDE to it's fullest.

---

