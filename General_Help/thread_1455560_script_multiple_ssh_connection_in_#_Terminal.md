---
title: "script: multiple ssh connection in # Terminal"
date: 2010-04-16
forum: General Help
---

### Post by issamneo on 2010-04-16
hi all i try to do a script that open 20 ssh connection each one in a # terminal. any help?
Thank you

---

### Post by cjhabs on 2010-04-16
> **issamneo said:**
> hi all i try to do a script that open 20 ssh connection each one in a # terminal. any help?
Thank you

I don't know how to do it with the Gnome terminal, but you can do it with xterm:
xterm -e ssh remote_hostname

---

### Post by KeyserSoze93 on 2010-04-16
What do you mean # terminal? I assume you mean an X terminal, because there are only 12 TTYs.

```

for i in $(<~/my_hosts.txt); do

xterm -e ssh $i&

done

```

---

### Post by issamneo on 2010-04-16
sorry i mean a new tab on my terminal
((the new tab when i click ctrl+MAJ+T))
i have try a for loop like this:

for i in 1 2 3 4 5 6 7 8 9 do

ssh 10.10.10.$i

done

but it open an ssh connection then when i exit the ssh connection it open the next one.
i want that it open a new tab on each iteration: and in that tab  it execute the ssh 10.10.10.$i
hope i was clear this time
i have try this:

for i in 61 62 63 64 
do
xterm -e ssh 10.10.10.$i&
#ssh 10.10.10.$i;
done


but it open a new terminal for each ssh connection, but i want all of them as tabs on my terminal.
Thank you for your help.

---

### Post by t0p on 2010-04-16
I believe the command ```
gnome-terminal --tab-with-profile=PROFILENAME
``` should do the trick. I suggest you check out ```
man gnome-terminal
``` for more info.

---

