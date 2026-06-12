---
title: "problem installing synaptic"
date: 2012-06-02
forum: General Help
---

### Post by hembrasalvaje on 2012-06-02
wondering if anyone could help me out with this. while i have a little command line experience i cant seem to get synaptic to install on ubuntu 12.04. i detest the ubuntu software center, and installing it from there is not working either as it says it has dependencies that cannot be installed. 
am getting the same problem in terminal as well


also all the instructions for copy and paste for terminals dont seem to be working for me for some reason. am on a laptop and only have the touchpad and 2 buttons. control-shift-c does not seem to want to work either

---

### Post by matt_symes on 2012-06-02
Hi

Open a terminal and type

```
sudo apt-get install synaptic
```

Enter your password. It will not be echoed to the screen.

If there are any errors then post them back here between code tage like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by Cheesemill on 2012-06-02
Can you type
```
sudo apt-get update && sudo apt-get install synaptic
```
into a terminal and post the errors you are getting please. We can't help without them :)

---

### Post by hembrasalvaje on 2012-06-02
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo apt-get install synaptic
```Enter your password. It will not be echoed to the screen.

If there are any errors then post them back here between code tage like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```Kind regards


```
 
reading package lists..... done
building dependency tree
reading dependency tree... done
some packages could not be installed. this may mean you have requested an impossible situation or if you are using an unstable distribution that some of the required packages have not yet been created or have been moved out of incoming.
the following may help to resolve the situation:

the following packages have unmet dependencies:
synaptic: depends: libept1.4.12 but it is not installable
E: unable to correct problems, you have held broken packages.


```

this is what comes up. had to manually type it in and is exactly what i was getting last night when i posted

Regards
Toni

---

### Post by hembrasalvaje on 2012-06-02
> **Cheesemill said:**
> Can you type
```
sudo apt-get update && sudo apt-get install synaptic
```into a terminal and post the errors you are getting please. We can't help without them :)



ok thankyou your bash line helped fix the problem. thankyou. for future reference do you have any idea how i can get the copy and paste to work from terminal screen so that rather than labouriously typing it all out i can copy and paste?

Regards 
Toni

---

### Post by Cheesemill on 2012-06-02
Select the text with your mouse and then right-click and copy.

To paste just hit right-click then paste.

---

### Post by hembrasalvaje on 2012-06-02
> **Cheesemill said:**
> Select the text with your mouse and then right-click and copy.

To paste just hit right-click then paste.

done but not working for me. not sure what i am doing wrong

---

