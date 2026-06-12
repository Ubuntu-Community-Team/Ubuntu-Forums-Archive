---
title: "What is the command for openibg an application in terminal on the main menu?"
date: 2009-07-09
forum: General Help
---

### Post by phr33k-dc on 2009-07-09
what the command? because i want to create a startup application but it runs in terminal but i just dont know the ligo...

i presume its something like gmone-terminal -rkhunter --check
thats the the program by the way -rkhunter

pls it would be a great help and its an easy to fix problem.
thanks

---

### Post by phr33k-dc on 2009-07-09
pls pls pls im desperate

---

### Post by phr33k-dc on 2009-07-09
bump

---

### Post by Nexusx6 on 2009-07-09
I don't know if I really understand your question, you didn't explain much, but I think what you're asking is how to start a program from terminal?

If that's it, usually you can just type the name of the program in the terminal.

```
kate
```
for example, will launch kate, and any messages kate outputs will be shown in that the terminal window that you launched it from.

---

### Post by phr33k-dc on 2009-07-09
thanks for the reply but i ment lets say if it was a link on the panel. wat would the commend be if it was a program that only ran in terminal?
for example if something needed java to run you would say "java -jar...etc so wat would it be for terminal?

---

### Post by phr33k-dc on 2009-07-09
or if its easier to understand imagine it was in "run" and you wanted to launch the program

---

### Post by credobyte on 2009-07-09
Then it would be a shell script ( in most cases ) :p

---

### Post by phr33k-dc on 2009-07-09
what does that that mean for me? can i still use a command? what is the command?

---

### Post by nikhilk on 2009-07-09
> **phr33k-dc said:**
> or if its easier to understand imagine it was in "run" and you wanted to launch the program

If you want to launch something (a shell script or an executable) from a shell you can use the command
```
bash <command>
```

If you want to run a complex command like you said in your example java -jar <jarfile> you can specify the command to bash like this (remember to enclose your command in quotes)
```
bash -c <your command>
```

You can specify multiple quoted commands by separating them via a semi-colon ';'
e.g bash -c "java -jar file1.jar; java -jar file2.jar"

---

### Post by credobyte on 2009-07-09
```
echo "echo 'I'm a shell script!'" >> $HOME/myscript.sh && chmod +x $HOME/myscript.sh
```

Command for main menu ( replace username ) :
```
/home/username/myscript.sh
```

---

### Post by phr33k-dc on 2009-07-09
it doesnt work!!! the command i want to run is:

sudo rkhunter --check

but i want to make it as a startup application.

so i need the command

---

### Post by nikhilk on 2009-07-09
> **phr33k-dc said:**
> 
but i want to make it as a startup application.

so i need the command

Take a look at [this]("https://help.ubuntu.com/community/AddingProgramToSessionStartup"). Does it help?

---

### Post by nikhilk on 2009-07-09
Actually, for your case, it would be better to run it as root before any users have logged in. Try adding that command (without sudo i.e. only rkhunter --check) to /etc/rc.local

---

### Post by nothingspecial on 2009-07-09
Go into your menu.

Go system > preferences > main menu

Navigate to the entry you want 

Right click on it and choose properties.

This will show you the command that opens the app

Add that command to system > preferences > startup applications

---

### Post by phr33k-dc on 2009-07-09
no sorry didnt have it there. it could be my fault for not explaining it prop.

i have a application the i can run in terminal. the command for the program in terminal is rkhunter --check.

i want to make it a start  program but i need the command that opens up terminal and automatically runs the program without me having to type it in. hence to value of having a startup program. any ideas?

---

### Post by nothingspecial on 2009-07-09
sorry 

```
gnome-terminal -x rkhunter --check
```

---

### Post by phr33k-dc on 2009-07-09
thats waht i was looking for except when i typed it in i just saw a flash of a window and it dissapeared????

---

### Post by Villiam on 2009-07-09
I recommend you check these documentation [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) for understanding the usage of Terminal.

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by phr33k-dc on 2009-07-09
thanks nothingspecial i added sudo to it and it works great.
solved!!!!!!!

---

