---
title: "Bash problem"
date: 2011-04-19
forum: General Help
---

### Post by gizmmo on 2011-04-19
Hello

i am new to Ubuntu and i am trying diferent things. Since i don't want to test things on a real machine, i installed it on a virtual machine. I am curently runing latest version of Ubuntu in virtualbox.

My problem is i can't modify bash prompt and save it that way.
I am looking for a simple prompt, i.e. PS1="X:\w> "
If i type it in, it works but if i try to add it to /etc/bash.bashrc , nothing happends

After adding the line, i do >exec bash and the prompt gets reverted to the default prompt. I've read around and other people saved it exactly the way i'm trying to. Only diference is they don't run Ubuntu as a virtual machine.

I would like to know how can i save the prompt please. Any help will be apreciated

---

### Post by Crusty Old Fart on 2011-04-19
Try changing your prompt in ~/.bashrc instead of /etc/bash.bashrc
Then try reloading it in the same terminal window using the following command:
```

source ~/.bashrc

```What happens?

---

### Post by gizmmo on 2011-04-19
it resets to the default prompt

---

### Post by Crusty Old Fart on 2011-04-19
I edited my post...I think I changed it while you were following what I had written originally.
Try it again with the new instructions.

What happens when you make your changes in ~/.bashrc instead of /etc/bash.bashrc?

---

### Post by gizmmo on 2011-04-19
i've been looking to modify that for a while but i don't seem to have a .bashrc in my ~/

strange...

---

### Post by Crusty Old Fart on 2011-04-19
> **gizmmo said:**
> i've been looking to modify that for a while but i don't seem to have a .bashrc in my ~/

strange...
Not so strange, really. Just make one. Then put your PS1 mod in it. It should get loaded last and overwrite the default PS1.

Capice?

---

### Post by gizmmo on 2011-04-19
seems to work but it still doesn't solve my problem. after making the file in ~/ and using source ~/bash.bashrc, the prompt changes BUT after i close the terminal and reopen it, the prompt goes back to the default prompt.


source /etc/bash.bashrc also seem to work and change my prompt. same problem tho, after i close and reopen the terminal, prompt goes back to the default setting.

---

### Post by Crusty Old Fart on 2011-04-19
> **gizmmo said:**
> seems to work but it still doesn't solve my problem. after making the file in ~/ and using source ~/bash.bashrc, the prompt changes BUT after i close the terminal and reopen it, the prompt goes back to the default prompt.

The file you need to make in ~/ is: [COLOR=Blue]**.bashrc**[/COLOR] NOT: **[COLOR=Red]bash.bashrc[/COLOR]**

You can have one line in ~/.bashrc:
```

PS1="X:\w> "

```Then you can reload it with:
```

source ~/.bashrc

```I'm guessing you made a file: ~/bash.bashrc and put your PS1 mod in it. If that's right, then you can just rename it to ~/.bashrc and then reload it like this:
```

mv ~/bash.bashrc ~/.bashrc
source ~/.bashrc

```That should work.

---

### Post by gizmmo on 2011-04-19
awesome. it works. thanks a lot.

one more question/curiosity if i may. after the rename, the file is hidden?

ls doesn't show it but i can edit it just fine :)

anyway, thanks for the help.

---

### Post by Crusty Old Fart on 2011-04-19
> **gizmmo said:**
> awesome. it works. thanks a lot.

one more question/curiosity if i may. after the rename, the file is hidden?

ls doesn't show it but i can edit it just fine :)

anyway, thanks for the help.

It's hidden because it's supposed to be. Hidden files begin with dots.

If you're in a shell and issue the following command:
```

ls -al

```You'll see all of the files in the present working directory, including the hidden ones.

Glad you go it working and...
You're mighty welcome.

All the best,

Crusty

---

### Post by Crusty Old Fart on 2011-04-19
Come to think of it, you may have always had a ~/.bashrc file but never knew it if you were using ls without the -a option.

If you made a ~/bash.bashrc file, and then renamed it to ~/.bashrc, you'd have blown away any original ~/.bashrc file that may have existed.

That would be a bummer.

---

### Post by gizmmo on 2011-04-20
it doesn't really matter since i'm working on a Linux virtual test machine :)

---

### Post by Crusty Old Fart on 2011-04-20
> **gizmmo said:**
> it doesn't really matter since i'm working on a Linux virtual test machine :)
I sort of suspected as much. I  was getting ready to upload the original .bashrc file that came with my Lucid distro but thought that since you are just getting started with Linux, you will get the default .bashrc back when you do your next reinstall. You'll probably reinstall dozens of times before you get to the place where you're enough of a Linux geek that you don't break things as a result of experimenting. However, If you want the original Lucid .bashrc, I'll put it up here on your asking.

Have fun,

Crusty

---

### Post by nothingspecial on 2011-04-20
> **Crusty Old Fart said:**
> Come to think of it, you may have always had a ~/.bashrc file but never knew it if you were using ls without the -a option.

If you made a ~/bash.bashrc file, and then renamed it to ~/.bashrc, you'd have blown away any original ~/.bashrc file that may have existed.

That would be a bummer.

Not really, there's a default one in /etc/skel. If you ever mess up your .bashrc simply

```
cp /etc/skel/.bashrc ~/
```

That will restore everything to the default settings. Of course if you have a highly customized .bashrc you should back it up anyway.

---

### Post by Crusty Old Fart on 2011-04-20
To nothingspecial:

Nice.

Thanks.

---

