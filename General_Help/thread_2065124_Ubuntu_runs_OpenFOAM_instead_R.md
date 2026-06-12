---
title: "Ubuntu runs OpenFOAM instead R"
date: 2012-10-01
forum: General Help
---

### Post by zediks on 2012-10-01
Hello!

I used R language software just by typing R in a terminal.

I have installed OpenFOAM recently [http://www.openfoam.org/download/ubuntu.php](http://www.openfoam.org/download/ubuntu.php)
and now when I type R it runs OpenFoam(with an error).


I don't have a lot of experience with Ubuntu.
Does anybody know how I can try to fix that?

#
I have installed OpenFOAM in the next way:
VERS=$(lsb_release -cs) 
sudo sh -c "echo deb [http://www.openfoam.org/download/ubuntu](http://www.openfoam.org/download/ubuntu) $VERS main > /etc/apt/sources.list.d/openfoam.list"
sudo apt-get update
sudo apt-get install openfoam211
sudo apt-get install paraviewopenfoam3120

---

### Post by ElSafti on 2012-10-01
Hello,

It seems that there is a solver in OpenFOAM called "R". All you have to do is to remove the line in the "~/.bashrc" that you added during installation:
```

. /opt/openfoam211/etc/bashrc

```
By removing this line the terminal will load without OpenFOAM aliases (shortcuts). This way you can run R that was defined before OpenFOAM installation. You would need to add a line to the ~/.bashrc file to make an alias for running OpenFOAM.
```

alias OF211='. /opt/openfoam211/etc/bashrc'

``` 

so when you write OF211 in the terminal you have OpenFOAM ready to run and you can have another terminal open for R.

Another solution would be to define an alias for R in the ~/.bashrc file after the ". /opt/openfoam211/etc/bashrc" line. To know where is the binary (executable) for R type:
```

$ which R

```

For further questions I think the CFDonline forum is more suitable.

Regards
Hisham

---

### Post by zediks on 2012-10-01
Thanks a lot!

---

