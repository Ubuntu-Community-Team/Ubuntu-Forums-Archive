---
title: "Exporting the 'pwd' cmd to a $ variable"
date: 2011-07-25
forum: General Help
---

### Post by max_sph on 2011-07-25
Hey guys,
I'm a bit new with the bash shell system for unix.
Basically, I'm trying to create a file (using the 'touch' cmd) in terminal that inherit its name from the working directory folder I am currently operating in.

So, say I was in a folder called viewCase, I need to create a file that automatically has the name viewCase.extension. The problem is that I can't use a command in my .bashrc file such as:
export WORK=''\w" or "\W" like when exporting PS1 to change the shell cmd prompt, because it just exports the string as \w rather than the actual working directory.

Can anyone offer a solution to this?

Many thanks :-)

Max

---

### Post by idoitprone on 2011-07-25
> **max_sph said:**
> Hey guys,
I'm a bit new with the bash shell system for unix.
Basically, I'm trying to create a file (using the 'touch' cmd) in terminal that inherit its name from the working directory folder I am currently operating in.

So, say I was in a folder called viewCase, I need to create a file that automatically has the name viewCase.extension. The problem is that I can't use a command in my .bashrc file such as:
export WORK=''\w" or "\W" like when exporting PS1 to change the shell cmd prompt, because it just exports the string as \w rather than the actual working directory.

Can anyone offer a solution to this?

Many thanks :-)

Max
the ` are not quote but the character above the tab
```

$var=`pwd`
$ echo $var
/home/chicken
```

---

### Post by AlphaLexman on 2011-07-25
```
pwd
```
and
```
echo $PWD
```
Are the same thing.

---

### Post by idoitprone on 2011-07-25
> **AlphaLexman said:**
> ```
pwd
```and
```
echo $PWD
```Are the same thing.

yep yep yep. I kidda know it redudent, but whatever the op wants. I give it to him lol.

---

### Post by mikejonesey on 2011-07-25
for those that don't know and want to know, you can echo $PWD because it's an environment variable, you can see you current environment variables by typing env... :)

---

### Post by sisco311 on 2011-07-25
Welcome to the forums!

Is this your homework?

---

### Post by jamesisin on 2011-07-25
I suppose, based on what you are trying to accomplish, you'll want to do something like this:

```
$path=`pwd`
foldername=$( basename "$path" )
touch "foldername".extension
```

---

### Post by sisco311 on 2011-07-25
Instead of basename I would use parameter expansion.

touch updates the atime and mtime of one or more files. I would use > to create a new file.

```
> "${PWD##*/}.ext"
```

@OP:
and to answer your original question: [http://mywiki.wooledge.org/CommandSubstitution](http://mywiki.wooledge.org/CommandSubstitution)

---

### Post by jamesisin on 2011-07-25
> **sisco311 said:**
> Instead of basename I would use parameter expansion.

touch updates the atime and mtime of one or more files. I would use > to create a new file.

```
> "${PWD##*/}.ext"
```

That works nicely.  Thanks.

---

### Post by max_sph on 2011-07-26
Thanks for all the help peeps! :-)

touch ${PWD##*/}.ext works good, but can't be in my .bashrc file (for, say, an alias) because it just uses the directory where I guess the bashrc is sourced every time terminal is opened, eg, home dir.

so, I created an alias to a .bat file with contents:

dirName=${PWD##*/}
fileName="$caseName.ext"
touch $fileName

then using the alias works good!

Thanks again everyone!

EDIT:
Yeah this is kind of homework! Im studying computational fluid dynamics for my masters, and currently using OpenFOAM on my macbook to do a few simulations. But unfortunately I can only run Ubuntu through VMWare or Parallels... but I want to run my simulations native so its that wee bit quicker :p Perhaps I'm a bit lazy... lol
Thanks for the warm welcome too!

---

