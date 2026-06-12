---
title: "Change owner of documents"
date: 2009-12-29
forum: General Help
---

### Post by toineurlings on 2009-12-29
Hi, 
After some **** with VMware and losing my ctrl is made me a new user and with "sudo nautilus" copied all my not hidden files to my new personal map. But after that I could only read them, because root is the owner, I can only change permitions for everyone but I don't want everyone to be able to get into my documents.

So how do I change the ownership from these documents?
tnks

---

### Post by doas777 on 2009-12-29
well, changing ownership is somthing you can't do via the gui right now.
so go to Applications -> Accessories -> Terminal
the command you want is chown. here is the syntax

chown [-R] <user>:<usergroup> <file/folderpath>
(replace all values in <>; [] are optional; -R will cause it to process all subfiles/subdirs on the path)

so if i wanted to assign ownership of all files under /thing1 to myself, I would enter
```

sudo chown -R doas777:doas777 /thing1

```

---

### Post by toineurlings on 2009-12-29
but is it good to do this with all folders in my personal map? Also with the hidden ones, with program files? Tanks for a soon response

---

### Post by doas777 on 2009-12-29
> **toineurlings said:**
> but is it good to do this with all folders in my personal map? Also with the hidden ones, with program files? Tanks for a soon response

map? no it's not good for everything, only for the specific folder where your files are. do not run chown on / or another folder that is not primarily userdata.

---

### Post by toineurlings on 2009-12-29
> **doas777 said:**
> map? no it's not good for everything, only for the specific folder where your files are. do not run chown on / or another folder that is not primarily userdata.

No, I mean my personal map "/home/toineurlings" there are also hidden folders!

---

### Post by toineurlings on 2009-12-29
> **doas777 said:**
> well, changing ownership is somthing you can't do via the gui right now.
so go to Applications -> Accessories -> Terminal
the command you want is chown. here is the syntax

chown [-R] <user>:<usergroup> <file/folderpath>
(replace all values in <>; [] are optional; -R will cause it to process all subfiles/subdirs on the path)

so if i wanted to assign ownership of all files under /thing1 to myself, I would enter
```

sudo chown -R doas777:doas777 /thing1

```


The way of writing I don't get fully, 
I need to change the owner of the map "/home/toineurlings" my username is "toinurlings"

---

### Post by doas777 on 2009-12-29
> **toineurlings said:**
> No, I mean my personal map "/home/toineurlings" there are also hidden folders!
so your entire home is owned by root?
it is safe to change ownership of your home, but there are several files that will require special permissions. hopefully they were not changed, so when you change the owner back to <user>:<user> everything will work out.

---

### Post by toineurlings on 2009-12-29
no, I first had an account "toine" but because I had a problem I couldn't solve I made a new account "toineurlings". I copied all the not hidden document from "toine" with "sudo nautilus" to "toineurlings" but now root is owner of the home-map "toineurlings"

---

### Post by toineurlings on 2009-12-29
but when I need to change the owner of the map "/home/toineurlings" and my username is "toinurlings". What's the command?

---

### Post by sanderd17 on 2009-12-29
If you want to change the owner of your home directory, execute the command
```

sudo chown -R toineurlings:yourGroup /home/toineurlings

```
you do have to change yourGroup to the usergroup you use. 
After that, the home folder is owned by you but I can't say for sure if it's good to use with the hidden folders.

---

### Post by toineurlings on 2009-12-29
It said:

chown: kan geen toegang krijgen tot `/home/toineurlings/.gvfs&#8217;: Toegang geweigerd


(it cant get access to `/home/toineurlings/.gvfs&#8217;: access denied)

:confused:

Is it right my group is also toineurlings? It said in "users"

---

### Post by doas777 on 2009-12-29
> **sanderd17 said:**
> If you want to change the owner of your home directory, execute the command
```

sudo chown -R toineurlings:yourGroup /home/toineurlings

```you do have to change yourGroup to the usergroup you use. 
After that, the home folder is owned by you but I can't say for sure if it's good to use with the hidden folders.

in this specific case it would be:
```
sudo chown -R toineurlings:toineurlings /home/toineurlings
```
it will hit hidden files. 

after you are done running the command, post the output of 
```
ls -al ~
```

---

### Post by doas777 on 2009-12-29
> **toineurlings said:**
> It said:

chown: kan geen toegang krijgen tot `/home/toineurlings/.gvfs’: Toegang geweigerd


(it cant get access to `/home/toineurlings/.gvfs’: access denied)

:confused:

Is it right my group is also toineurlings? It said in "users"

yes in this case, your group is the same as your username. 

run the command with sudo to avoid the access denied.

---

### Post by toineurlings on 2009-12-30
with sudo it still says access denied :confused:

---

### Post by toineurlings on 2009-12-31
tried it again... it seems everything is alright, but it still says access denied:-k

---

