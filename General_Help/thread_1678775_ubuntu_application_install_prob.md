---
title: "ubuntu application install prob"
date: 2011-01-31
forum: General Help
---

### Post by nikhil_me on 2011-01-31
greetings!!!
i am not able to install pgadmin3 on ubuntu.i use macbook air so installing through wi-fi.
i am installing using the software centre. i am able to install other programs from there but not able to intstall pgadmin3. help plzzzz
thanx

---

### Post by mikewhatever on 2011-01-31
'Not able' is a phrase open to interpretation. Not able why? Does your finger get stuck right before clicking the 'Install' button, or do you get a bunch of errors?

---

### Post by dirghrabadia on 2011-01-31
>  Does your finger get stuck right before clicking the 'Install' button

:lolflag:

---

### Post by nikhil_me on 2011-01-31
not able means installation not starting. I already told i am able to install other apps (so fingers obviously not getting stuck)

---

### Post by mikewhatever on 2011-01-31
Try installing from a terminal window, hopefully you'll get a meaningful output.
```
sudo apt-get install pgadmin3
```

---

### Post by nikhil_me on 2011-01-31
done that
0% (waiting for headers)
doesn't proceed ahead!!!!!!

---

### Post by mikewhatever on 2011-01-31
Not quite sure what's going on there. It might also be helpful to know what version of Ubuntu you have.
Check with **less /etc/lsb-release**.

---

### Post by nikhil_me on 2011-01-31
ubuntu 10.10 maverick meerkat
i am also not able to install php5 (tried using terminal) . i tried to do it manually but it gives dependency not satisfiable. is there any file i am missing????
i am not even able to update it using update manager (updating is not proceeding) (though able to update using sudo apt-get update)

---

### Post by mikewhatever on 2011-01-31
Odd. Looks like something is wrong with the package manager or the repositories. Did you, perhaps, do a manual kernel upgrade?

---

### Post by nikhil_me on 2011-01-31
i am using ubuntu on vmware. i updated using sudo apt-get update nothing else

---

