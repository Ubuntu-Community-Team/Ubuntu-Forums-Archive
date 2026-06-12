---
title: "How to move files from one User Account to the other?"
date: 2009-12-22
forum: General Help
---

### Post by JoeyF on 2009-12-22
Ok, So i set up one User Account when i first installed Ubuntu. But i recently made a new one with the privileges of "Desktop user" and i want to copy my music from the (Joey) account to the new one. But i get a permissions error when i try to do it from both accounts. Like When i try to do it from my Joey account  i get "permission denied".


Will i have to do it from the terminal? what would be the code?


Thanks.

---

### Post by synapsys on 2009-12-22
```
sudo cp /home/user1/music/* /home/user2/music/
```

or you can use:

```
gksu nautilus
```

to open a file manager with root permissions and copy over from there. Be careful with this one....

---

### Post by audiomick on 2009-12-22
If you open nautilus as a super user
> gksu nautilus

you should be able to do what you need.

---

### Post by synapsys on 2009-12-22
> **audiomick said:**
> If you open nautilus as a super user


you should be able to do what you need.

great idea.................................................................................................................................................

---

### Post by JoeyF on 2009-12-22
I tried ```
sudo cp /home/joey/Music/* /home/autumn/Music/
``` it acts like it worked(Showing the file names in the terminal) but the files are not there. only a picture that i had in my Music folder.

---

### Post by audiomick on 2009-12-22
> **synapsys said:**
> great idea.................................................................................................................................................

must be. you thought of it too, didn't you? ;)
You got your post in quicker than me...

---

### Post by JoeyF on 2009-12-22
I tried the natilous command but i got some errors in the terminal and when it came out the user folders weren't there.

---

### Post by audiomick on 2009-12-22
> **JoeyF said:**
> I tried the **[COLOR="Red"]natilous[/COLOR]** command but i got some errors in the terminal and when it came out the user folders weren't there.
did you spell it right?

nautilus

---

### Post by JoeyF on 2009-12-22
Yes, I tried gksu-nautilus

---

### Post by JoeyF on 2009-12-22
I'm kind of scared to try natiolus again because when i did my cd burner opended. lol

---

### Post by audiomick on 2009-12-22
> **JoeyF said:**
> Yes, I tried gksu**[COLOR="Red"]-[/COLOR]**nautilus

still wrong, if that's what you did.

```
gksu nautilus

```

that your cd drive opened is odd...:confused:

---

### Post by synapsys on 2009-12-22
> **JoeyF said:**
> Yes, I tried gksu-nautilus
 
It's 

```
gksu nautilus
```

not 

```
gksu-nautilus
```

and try this

```
sudo cp -r /home/joey/Music /home/autumn/Music
```

---

### Post by doas777 on 2009-12-22
ok, it is 

hit Alt + F2
and enter
```
gksu nautilus
```
without hyphens or 'o's. 

when the window opens, it will be in roots home dir (/root) not yourown, so you will have to navigate to /home/<username>/music.

---

### Post by JoeyF on 2009-12-22
> **synapsys said:**
> It's 

```
gksu nautilus
```

not 

```
gksu-nautilus
```

and try this

```
sudo cp -r /home/joey/Music /home/autumn/Music
```


The last code worked.! thanks

---

