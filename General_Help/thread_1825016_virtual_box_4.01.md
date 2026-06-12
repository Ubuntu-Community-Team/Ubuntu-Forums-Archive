---
title: "virtual box 4.01"
date: 2011-08-14
forum: General Help
---

### Post by cowboy7305 on 2011-08-14
i have loaded V/B 4.01 and also the matching extension pack have run and it installed ok ,i think ,when i open V/B and run windows the mouse stays captured in the windows box of V/b until i press Ctrl right 
who do i undo this and have full controle of mouse over both ubuntu and V/D

---

### Post by haqking on 2011-08-14
> **cowboy7305 said:**
> i have loaded V/B 4.01 and also the matching extension pack have run and it installed ok ,i think ,when i open V/B and run windows the mouse stays captured in the windows box of V/b until i press Ctrl right 
who do i undo this and have full controle of mouse over both ubuntu and V/D

install Vbox Additions from the menu.

It will mount an image and then run the install

---

### Post by cowboy7305 on 2011-08-14
Ok have done that and i now have mouse comtrole 
 next part i have no usb showing up telles me i have to put in vboxusers groups where is that in the system

---

### Post by haqking on 2011-08-14
> **cowboy7305 said:**
> Ok have done that and i now have mouse comtrole 
 next part i have no usb showing up telles me i have to put in vboxusers groups where is that in the system


go to users and groups  at system>adminstration>users and groups

create a new group called vboxusers and add yourself to the group

---

### Post by cowboy7305 on 2011-08-14
I have been to Admin user group made a new user called vboxusers
so that is mow 2 users on computer one being my own log in to ubuntu then this vboxusers
question what mane are people talking about to go into vboxusers group and how do i put it in to vboxusers ,sorry if this sounds stupid but i cant see how its done

---

### Post by haqking on 2011-08-14
> **cowboy7305 said:**
> I have been to Admin user group made a new user called vboxusers
so that is mow 2 users on computer one being my own log in to ubuntu then this vboxusers
question what mane are people talking about to go into vboxusers group and how do i put it in to vboxusers ,sorry if this sounds stupid but i cant see how its done

i refer you to my post above.

i never said create a user called vboxusers in the admin group

I said create a GROUP called vboxusers

then add your own account which you login with into that group

---

### Post by Joebewan on 2011-08-14
Just to be certain, you are running the PUEL version downloaded from virtualbox.org, correct ??  The version in the repositories doesn't support USB.

---

### Post by haqking on 2011-08-14
> **Joebewan said:**
> Just to be certain, you are running the PUEL version downloaded from virtualbox.org, correct ??  The version in the repositories doesn't support USB.

it does with extensions pack which he already said he has installed.

His problem seems to be he is not creating the vboxusers group correctly though hopefully he has by now

the one in the repos is 3.1.8 and the title of his thread is 4.01

---

