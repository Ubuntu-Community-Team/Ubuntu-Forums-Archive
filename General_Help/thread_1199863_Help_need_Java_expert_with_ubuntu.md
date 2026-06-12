---
title: "Help need Java expert with ubuntu"
date: 2009-06-29
forum: General Help
---

### Post by billyjack on 2009-06-29
I have a dell mini 9 with ubuntu.  I do however need to access my work site that is windows based and uses Sun Java virtual machine.. I can pull the site up, but it will not log me in because it needs java.  Is there a way I can download Java onto the ubuntu, or download it to an outside drive in order to access this site?  Please help

thanks

---

### Post by Idefix82 on 2009-06-29
Open the terminal and type in
```
sudo apt-get update
sudo apt-get install openjdk-6-jre
```
providing your login password when you are asked for it.

---

### Post by billyjack on 2009-06-29
Sorry to sound dense, but how do I open the terminal?

---

### Post by Idefix82 on 2009-06-29
Applications->Accessories->Terminal

---

### Post by billyjack on 2009-06-29
Thank you so very much.. I will give this a try.

:))

---

### Post by billyjack on 2009-06-29
This did not work.. the specifications on the site I need to load are :

Mozilla Firefox 2.0 or greater 

Java Virtual Machine: Latest Available from Sun Microsystems 

Is this something I can attain, or is there a way to get around it?

Any info would be helpful.

---

### Post by zero777zero on 2009-06-29
^spambot

@billyjack: go into Add/Remove, make sure you have "Show" set to "All Available Applications", type in "Java" and "Sun Java 6 Runtime" should come up, check the box next to it click "Apply Changes"

---

### Post by XCan on 2009-06-29
> **Idefix82 said:**
> Open the terminal and type in
```
sudo apt-get update
sudo apt-get install openjdk-6-jre
```
providing your login password when you are asked for it.

I recommend that you install sun's releases though if you want to save yourself some headache (especially the firefox plugin). OpenJDK is very dodgy at its current state:
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---

### Post by billyjack on 2009-06-29
I did that in applications, typed in java and it is not there.. even after I loaded it like the first person told me to.  any more suggestions?

---

### Post by billyjack on 2009-06-29
is this going to use a lot of memory..??

---

### Post by Sub101 on 2009-06-29
Did you manage to install the sun version of java as in the previous post?

Once you have be sure to restart your browser and then try the site again.

---

### Post by askreet on 2009-06-29
> **billyjack said:**
> is this going to use a lot of memory..??

Applications which are installed on your computer take up disk space, not memory.

Memory is used by running applications.  Java is known for taking up a lot of memory while it is running.

Quite often you'll find people here will be helping you with commands run inside a terminal, that's what we're used to and it's how we use Linux on a day to day basis.

If you open a terminal and type:
```
java -version
```

Then press enter, what do you get?

---

### Post by billyjack on 2009-06-29
when I type in java -version I get "1.6.0_0"
openjdk runtime envirnment (build 1.6.0_0-bll)
openjdk client vm )build 1.6.0_0-bll, mixed mode, sharing)

I have not yet done what the previous person said to do to make it faster

---

### Post by billyjack on 2009-06-29
I have one more question for all of you helpers out there.  by adding the java that the first person told me to add, am I bogging down my computer?  Just asking because I dont want to cause anything to bog down.  I did get my website to work.. I had also added the firefox 2 web browser and it works like a charm.. so now wondering if I even needed to add that java.. what do you think?

---

### Post by XCan on 2009-06-29
If java isn't running it won't bog down your computer, but oviously, you need to run java if your app is written for java. If you're wondering if there are processes running related to java for no apparent reasons as in Windows, the answer is no.

---

