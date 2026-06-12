---
title: "Completely removing Java, then reinstalling - what do I select in Package Manager?"
date: 2011-09-15
forum: General Help
---

### Post by AlexOnVinyl on 2011-09-15
Hey folks,

I'm trying to uninstall Java, then reinstall it in Package Manager

I uninstalled sun JRE and OpenJDK but there are still a few left over,
what all do I uninstall from the list that I have attached?

---

### Post by fdrake on 2011-09-15
have you tried:
```

sudo aptitude reinstall java*

```
what exactly is the problem?

---

### Post by raja.genupula on 2011-09-15
click at that main jdk file in synaptic and choose mark for complete removal . it will all the things about the java .

or search java in search box , it will shows all the java pkgs.

but here also same Question , why do you wanna remove java ?

---

### Post by AlexOnVinyl on 2011-09-15
> **fdrake said:**
> have you tried:
```

sudo aptitude reinstall java*

```what exactly is the problem?

well Minecraft 1.8 isnt loading no matter how many times I've chmod'd it and other code related things that worked with the previous version

---

### Post by AlexOnVinyl on 2011-09-15
> **raja.genupula said:**
> click at that main jdk file in synaptic and choose mark for complete removal . it will all the things about the java .

or search java in search box , it will shows all the java pkgs.

but here also same Question , why do you wanna remove java ?

I'm reinstalling it.

did you look at my attachment? those are what are left, do I uninstall all those too?

---

### Post by fdrake on 2011-09-15
> **AlexOnVinyl said:**
> well Minecraft 1.8 isnt loading no matter how many times I've chmod'd it and other code related things that worked with the previous version

most of the errors that i have encountered with java are path related , programs cannot find (or find an older,only) java compiler.
in case the reinstall does not work, can you post the exact error msgs? run the app from the terminal.

---

### Post by AlexOnVinyl on 2011-09-15
> **fdrake said:**
> most of the errors that i have encountered with java are path related , programs cannot find (or finds an older one only) java compiler.
in case the reinstall does not work, can you post the exact error msgs? run the app from the terminal.

thats the thing. It doesn't load at all...lol.

---

### Post by raja.genupula on 2011-09-15
> **AlexOnVinyl said:**
> I'm reinstalling it.

did you look at my attachment? those are what are left, do I uninstall all those too?

man i am sorry , after that i had tried to edit the post but power gone . what ever reason is not the answer . 

```
sudo aptitude remove '~njava' 

```
remove all the java files

---

### Post by AlexOnVinyl on 2011-09-16
> **raja.genupula said:**
> man i am sorry , after that i had tried to edit the post but power gone . what ever reason is not the answer . 

```
sudo aptitude remove '~njava' 

```remove all the java files

Thank you. :)

---

### Post by raja.genupula on 2011-09-16
> **AlexOnVinyl said:**
> Thank you. :)

hey man , you are welcome . i hope its worked for you .

---

