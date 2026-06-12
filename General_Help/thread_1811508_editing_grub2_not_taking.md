---
title: "editing grub2 not taking"
date: 2011-07-25
forum: General Help
---

### Post by brad1138 on 2011-07-25
I have edited Grub2 a few different ways, but it still defaults to the top listing. I am trying to get it to default to Win7. I have used Startup manager and directly editing etc/default/grub (using sudo). The changes show when I go back to either method, but not during boot.

Thanks

---

### Post by Quackers on 2011-07-25
Which version of Ubuntu? I don't think startup manager works with 11.04.
After manual editing did you run sudo update-grub?

---

### Post by garvinrick4 on 2011-07-25
After you change /etc/default/grub you have to:
sudo update-grub
for them to take.

---

### Post by Quackers on 2011-07-25
Good morning GR4 :-)

---

### Post by brad1138 on 2011-07-25
> **Quackers said:**
> Which version of Ubuntu? I don't think startup manager works with 11.04.
After manual editing did you run sudo update-grub?

it is 11.04, No I didn't run sudo update.

Thanks.

---

### Post by Quackers on 2011-07-25
All fixed?

---

### Post by brad1138 on 2011-07-25
> **Quackers said:**
> All fixed?

No, running "sudo update-grub" didn't work either... Any ideas?

---

### Post by Quackers on 2011-07-25
Some users have had problems changing the default boot system in grub2 when using 11.04, it seems. Do a search as there have been a few recently. I believe all were resolved.
Are you editing the line ```
GRUB_DEFAULT=0
``` by changing the number after = ? Are you saving the file or just quitting it?

---

### Post by brad1138 on 2011-07-25
> **Quackers said:**
> Some users have had problems changing the default boot system in grub2 when using 11.04, it seems. Do a search as there have been a few recently. I believe all were resolved.
Are you editing the line ```
GRUB_DEFAULT=0
``` by changing the number after = ? Are you saving the file or just quitting it?

I am saving. it is that line although it was set at "GRUB_DEFAULT=6" the first time I saw it because I ran startup manager 1st and it changed it to 6(my Win 7 loader line is 6th). For the heck of it I tried 2, 4, 5, & 6, none worked.

I will search more tomorrow, bed time now.

Thanks again,
Brad

---

### Post by Quackers on 2011-07-25
Ok, goodnight :-)

---

### Post by garvinrick4 on 2011-07-25
> **Quackers said:**
> Good morning GR4 :-)
Quackers you up early across the pond. About 11 pm on the 24th still here. Good morning to you and have a nice day.

---

### Post by Quackers on 2011-07-25
Yes, the new puppy only wants to sleep when I'm awake :-) It doesn't allow me to sleep at night! I can't see that lasting long :wink:
It's 7-15am on the 25th here now.

---

### Post by brad1138 on 2011-07-25
Hello again, 

 I Have not been able to find anything that address my problem. The config files show the change to "6" in grub_default. When I change the delay time, that works, so I know I am doing it correctly. But still it highlights the first entry.

---

### Post by brad1138 on 2011-07-26
Got it figured out. It should have been 5, not 6. I never ran "sudo update-grub" on any one other than 6.

---

### Post by Quackers on 2011-07-27
Ah, did you forget to subtract 1 from the number your chosen OS is in the list?
If the top item in the list = GRUB_DEFAULT=0 then the 6th item in the list = GRUB_DEFAULT=5

---

### Post by brad1138 on 2011-07-27
> **Quackers said:**
> Ah, did you forget to subtract 1 from the number your chosen OS is in the list?
If the top item in the list = GRUB_DEFAULT=0 then the 6th item in the list = GRUB_DEFAULT=5

Ya, I would have thought of that, but "Start-up Manager" set it at 6 and I didn't question it. All is good now.

Thanks.

---

