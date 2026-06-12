---
title: "Asking for my password in the terminal"
date: 2010-05-21
forum: General Help
---

### Post by Newbez on 2010-05-21
So whenever I type in a command or try to install something through the terminal, it keeps asking for my password, so I type in it, but nothing comes up, but I press enter anyway but then it says that my password it wrong :/
What's going on? I'm completely new to Ubuntu by the way, been using for about 3 days now.

---

### Post by Tclarkie on 2010-05-21
in terminal when using sudo the letters will not come up when you type your pswd in, this is ok, make sure u get it right

---

### Post by sharath.puranik on 2010-05-21
You are typing your password wrong, there is no other reason for it to say password is wrong...

as for it showing nothing when you type in the password, do you really want your password to be shown when you are typing it in? It sort of defeats the purpose of passwords if you want it show in the terminal.

---

### Post by shaquille on 2010-05-21
I think the problem is solved.
So, marked is as solved.

---

### Post by 3rdalbum on 2010-05-21
Don't use 'su', use 'sudo'.

If you see directions that say something like:

```
su
make install
```

You'd instead do:

```
sudo make install
```

or

```
sudo -i
make install
```

Remember you don't usually need to install software through the terminal; you can use Synaptic Package Manager or Software Center.

---

### Post by Newbez on 2010-05-21
well when I type in my password, it doesn't show, it that how it's meant to be?

---

### Post by antenna on 2010-05-21
> **Newbez said:**
> well when I type in my password, it doesn't show, it that how it's meant to be?

Yes

---

### Post by gerf333 on 2010-05-21
mmm...

---

### Post by gerf333 on 2010-05-21
> **Newbez said:**
> well when I type in my password, it doesn't show, it that how it's meant to be?
  I don't think that

---

### Post by Nr90 on 2010-05-21
That is correct, you should only see a flashing bar.
Just type your password correctly and hit enter

---

### Post by tango_ninja on 2010-05-21
You will not see the password characters when typing in terminal.  They're hidden (probably due to security).  Just type the proper password and press 'enter.'  The only reason you should get an error is if you typed your password incorrectly.

---

### Post by TheGnomeOfMetal on 2010-05-21
its becuase it keeps your passwd unseen so if someone is remotely viewing you, they cant see your passwd. just make sure its right and press enter when you are done

---

