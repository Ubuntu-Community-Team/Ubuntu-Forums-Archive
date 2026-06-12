---
title: "Open a box terminal in ssh"
date: 2010-01-12
forum: General Help
---

### Post by endoglastic on 2010-01-12
is there any way to ssh into a computer and start something in a terminal so that it opens it up on that computer and runs it in another terminal in which i cant see using ssh. Like i want to start my cs server remotely but everytime i start it in ssh it will shut it down when i close my putty window. so is there a way to make it run on another terminal on the computer im connecting to so that the server wont close when i close putty?

---

### Post by DGortze380 on 2010-01-12
> **endoglastic said:**
> is there any way to ssh into a computer and start something in a terminal so that it opens it up on that computer and runs it in another terminal in which i cant see using ssh. Like i want to start my cs server remotely but everytime i start it in ssh it will shut it down when i close my putty window. so is there a way to make it run on another terminal on the computer im connecting to so that the server wont close when i close putty?

Fork the process.

./myscript 
- Will likely end when the session ends

./myscript &
- Forks the process so it will continue to run after your session ends.

---

### Post by endoglastic on 2010-01-12
ok what i do is
 
cd /hlds_surf    (right after clicking in filesystem)
 
and then type
 
./hlds_run -binary ./hlds_i686 -game cstrike -autoupdate +maxplayers 12 +port 27015 +map surf_ski_2 +pingboost 2 +ip 192.168.1.[FONT=Courier New][SIZE=1][FONT=Courier New][SIZE=1]30[/SIZE][/FONT][/SIZE][/FONT][SIZE=1] +tickrate 66[/SIZE]
 
[SIZE=1]and i put that & after like[/SIZE]
 
[SIZE=1]./hlds_run -binary ./hlds_i686 -game cstrike -autoupdate +maxplayers 12 +port 27015 +map surf_ski_2 +pingboost 2 +ip 192.168.1.[FONT=Courier New][SIZE=1][FONT=Courier New][SIZE=1]30[/SIZE][/FONT][/SIZE][/FONT][SIZE=1] +tickrate 66 &[/SIZE]
 
[SIZE=1]and it still closed, im sure im doing it wrong.[/SIZE]
 
or can you help me create a file so it does this.....[/SIZE]

---

