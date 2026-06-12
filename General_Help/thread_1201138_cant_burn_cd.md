---
title: "cant burn cd?"
date: 2009-06-30
forum: General Help
---

### Post by gfunkera on 2009-06-30
hi, im trying to burn a disc with information.. brasero crashes whenever i try to use it... theres nothing in the dmesg.. im using jaunty jackalope.. i also tried another burning software, that one crashed too..

i used to burn audio cds all the time in intrepid ibex.. 

also ive noticed that when the automatic updates occur, theres one listing under "reccomended updates" and its for brasero, but i cant download it because the check box next to it is grayed out... dunno if that helps but its an observation..

any help is appreciated! thanks!

---

### Post by ibutho on 2009-06-30
Which other burning app did you try? Gnomebaker seems to work ok for me (I've never been keen on Brasero). As for updates, try doing them in the terminal e.g.
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by John Private on 2009-06-30
I havent tested the Burning Programs because I am recent to Ubuntu but if the one built it use Gnomebaker.

---

### Post by synapsys on 2009-06-30
I guess it depends on the user. I've had good luck with gnomebaker and brasero, but absolutely terrible luck with k3b. Everytime I try to burn a cd or dvd with k3b, it fails halfway through.

---

### Post by alphacrucis2 on 2009-06-30
> **gfunkera said:**
> hi, im trying to burn a disc with information.. brasero crashes whenever i try to use it... theres nothing in the dmesg.. im using jaunty jackalope.. i also tried another burning software, that one crashed too..

i used to burn audio cds all the time in intrepid ibex.. 

also ive noticed that when the automatic updates occur, theres one listing under "reccomended updates" and its for brasero, but i cant download it because the check box next to it is grayed out... dunno if that helps but its an observation..

any help is appreciated! thanks!

Brasero seems to be very finnicky about burner hardware. I find that K3B works more reliably.

---

### Post by napzilla on 2009-07-02
I have been having similar problems burning CDs and DVDs since I upgraded to Jaunty. Both Brasero and Gnomebaker are unable to complete the burning process. I looked for some sort of clue in the session logs, but I don't see anything useful. Just in case, I have attached the log from a recent failed Brasero session (I cut out the redundant burning progress updates from the middle). I would much appreciate any insight into what seems to be going wrong, as I have found my inability to burn anything to CD somewhat crippling and frustrating. ](*,)

Thank you!

---

