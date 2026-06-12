---
title: "launcher for terminal script"
date: 2010-02-24
forum: General Help
---

### Post by sviesusisalus on 2010-02-24
hello. i'm new in shell scripting and launchers. i need to make a launcher for launching terminal, runing in it some commands and after completion i need to  close terminal window.
in terminal i need tu run such commands:

$fpc test.pas
$./test

and then it would be nice that the terminal automaticaly closes :) any suggestions ?

---

### Post by mac9416 on 2010-02-24
Howdy,

Maybe this will get you started:

```
gnome-terminal --execute fpc test.pas;./test
```

---

### Post by sviesusisalus on 2010-02-24
strange, for me it doesnt launch anything, terminal showed up once and then no reaction. i see that it runs for some time in system monitor, but no terminal window popup

```

fpc /home/justas/psc/test.pas; /home/justas/psc/test

```
directly from terminal runs perfect, but from launcher - nothing...

---

### Post by mac9416 on 2010-02-24
What about...

```
gnome-terminal --execute fpc /home/justas/psc/test.pas; /home/justas/psc/test
```

Is it possible that the command executed so fast that you didn't notice the terminal?

---

### Post by sviesusisalus on 2010-02-24
no that program in pascal is dummy, it stops execution and waits for input.
i tryed to launch this directly from terminal - works :D but launcher doesn't
```

gnome-terminal --execute fpc /home/justas/psc/test.pas; /home/justas/psc/test

```

---

### Post by doas777 on 2010-02-24
well, when you create the launcher, are you pulling down the Type list to change it from "Application" to "Application in Terminal"?

also, i've had better luck using a script than trying to pass args to gnome-terminal. it would be like:
```

#!/bin/bash
fpc test.pas
./test

```

---

### Post by sviesusisalus on 2010-02-24
APPLICATION IN TERMINAL did no effect, terminal window now stays on for longer and then exits and there is no output

---

### Post by d3v1150m471c on 2010-02-24
Write the script
```

#!/bin/bash
echo "hello world"
exit 0

```
Now save this script. I use my home folder because I don't have to type a path to execute it.
then:
```

chmod +x /path/to/your/file

```
Create a custom launcher by right clicking the panel and selecting the option. For the command entry put
```

gnome-terminal -e ./path/to/your/file && pkill gnome-terminal

```
Let me know if your having any trouble.

---

### Post by sviesusisalus on 2010-02-24
> **doas777 said:**
> well, when you create the launcher, are you pulling down the Type list to change it from "Application" to "Application in Terminal"?

also, i've had better luck using a script than trying to pass args to gnome-terminal. it would be like:
```

#!/bin/bash
fpc test.pas
./test

```

shell script is not suitable for me, it crashes my program. i need simple command line

---

### Post by d3v1150m471c on 2010-02-24
are you trying to execute it with a terminal instead of the launcher. is that what you mean?

---

### Post by d3v1150m471c on 2010-02-24
Secondly, I don't know if linux will even execute .pas language. I could be wrong. I think it needs to be .p and not .pas as well.

---

### Post by sviesusisalus on 2010-02-24
> **d3v1150m471c said:**
> are you trying to execute it with a terminal instead of the launcher. is that what you mean?
i need a launcher that opens terminal,then runs in it fpc compiler and then the compiled binary

---

### Post by d3v1150m471c on 2010-02-24
I'm not familiar with the pascal compiler or how to run pascal in linux. Those are two things you'll have to know. You'll need to add the two commands to the bash script after the shebang. After you give the script executable status with chmod then you can create the launcher. I covered how to do all of this in my original post.

---

### Post by sviesusisalus on 2010-02-24
i'll use two lines instead of one, it will open allot terminals(it doesn't matter for now)
first line:
```

gnome-terminal --execute fpc /home/justas/psc/test.pas 
```

and then:
```

gnome-terminal --execute /home/justas/psc/test 
```

for small compilations it would be the best choise, but if someone could manage it to run in one window this would be perfect :)

---

### Post by sviesusisalus on 2010-02-24
> **d3v1150m471c said:**
> I'm not familiar with the pascal compiler or how to run pascal in linux. Those are two things you'll have to know. You'll need to add the two commands to the bash script after the shebang. After you give the script executable status with chmod then you can create the launcher. I covered how to do all of this in my original post.
i managed to do it too..
pascal is not the main idea, im writting compiller for my neighbour. and there is one problem with shell script: in this case my program will have to create shell script(containing all the paths and etc.) and then run it... making it possible to run in one command line would be the best choise.

shell script:
```

#!/bin/bash
fpc /home/justas/psc/test.pas
chmod +x /home/justas/psc/test
/home/justas/psc/test

```

---

### Post by d3v1150m471c on 2010-02-24
```

#!/bin/bash
fpc /home/justas/psc/test.pas
chmod +x /home/justas/psc/test
/home/justas/psc/test

```/home/justas/psc/test needs to be 
```

chmod +x /home/justas/psc/test.[COLOR=Red]pas[/COLOR]
[COLOR=Red]codetorunpascallanguage[/COLOR][SIZE=3][COLOR=Red] [SIZE=5].[/SIZE][/COLOR][/SIZE]/home/justas/psc/test.[COLOR=Red]pas
[/COLOR]
```

---

### Post by d3v1150m471c on 2010-02-24
For the program to create the shell script in bash:
```

[COLOR=Blue]#!/bin/bash
echo [/COLOR]'[COLOR=Red]#!/bin/bash
echo "hello world"
exit 0[/COLOR]' [COLOR=Blue]> /path/to/test
chmod 755 /path/to/test
./path/to/test
exit 0[/COLOR]

```

---

### Post by sviesusisalus on 2010-02-25
thanks for help i have already solved it :)
no shell script needed, just some launchers

this is the pascal code:
```

procedure TForm1.MenuItem6Click(Sender: TObject);
          var
          AProcess:TProcess;
begin
     AProcess := TProcess.Create(nil);
     AProcess.CommandLine :='fpc ' + /home/justas/psc/test.pas;
     AProcess.Options := AProcess.Options + [poWaitOnExit, poUsePipes];
     AProcess.Execute;
     AProcess.Free;
     AProcess := TProcess.Create(nil);
     AProcess.CommandLine :='gnome-terminal -e /home/justas/psc/test';
     AProcess.Options := Aprocess.Options + [poWaitOnExit];
     AProcess.Execute;
     AProcess.Free;
end;               

```

---

