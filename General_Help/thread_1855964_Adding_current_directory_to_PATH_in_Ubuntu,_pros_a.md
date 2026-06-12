---
title: "Adding current directory to PATH in Ubuntu, pros and cons?"
date: 2011-10-07
forum: General Help
---

### Post by L a r r y on 2011-10-07
Say I open a command-line Terminal and navigate to my web site's cgi-bin folder, where I want to run some Perl scripts in the Terminal. .  I can now just type the Perl command, but for the system to find it, I need to preface it with a dot-slash to provide a relative reference to the current directory:```
./hello.cgi
```

I am familiar with a quarter-century of MS-DOS and Microsoft Windows, and if I follow the procedure outlined above, I can execute the script or program file in the current directory by just typing its name. . A slight twist here in Ubuntu Linux, that if I type just the name, the system cannot find the command.

In MS-DOS or Windows, the PATH includes the current directory, but in Ubuntu, it does not include the current directory.

I could solve this easily enough by adding "." to the PATH environment variable.

Is there any particular reason of security, or otherwise, that would dictate that I should not include the current directory in the PATH environment variable string?

Thanks for the advice!

---

### Post by L a r r y on 2011-10-07
**_Security Risk to add . (Current Directory) to PATH_**

I performed yet another Google search after posing my question and arrived at a thread from a C++ compiler, who, like me, found it necessary to hit ./ to preface his file name.

See [this Ubuntuforums thread]("http://ubuntuforums.org/archive/index.php/t-370477.html").

---

### Post by hwttdz on 2011-10-07
To summarize the objection in the other thread, they said you could put "rm -rf" in a file named ls in the current directory and give it executable permissions.  And then when you were to type ls in the current directory it would delete everything in the current directory.  And further they stated this constitutes a security risk.

1) This is not a security risk, if I want to make a file named ls that will remove all my files in a directory and name it "ls" I should be able to.  It would constitute a security risk if it somehow performed some action that my user does not have permissions to perform.

2) It is actually saving you from prefacing the command with the "./"

3) You could add your current directory to the end of your path instead of the beginning, so you couldn't override commands in /bin /usr/bin ....

All of that said I don't add the current directory to my path.  I keep a ~/bin where I put my own scripts and program, I also keep a ~/bin32 and ~/bin64 where I put more updated versions of things I can find in /bin or /usr/bin or /usr/local/bin or ....  And I run the which and type commands frequently.

---

### Post by L a r r y on 2011-11-12
> **hwttdz said:**
> To summarize the objection in the other thread, they said you could put "rm -rf" in a file named ls in the current directory and give it executable permissions.  And then when you were to type ls in the current directory it would delete everything in the current directory.  And further they stated this constitutes a security risk.

1) This is not a security risk, if I want to make a file named ls that will remove all my files in a directory and name it "ls" I should be able to.  It would constitute a security risk if it somehow performed some action that my user does not have permissions to perform.

2) It is actually saving you from prefacing the command with the "./"

3) You could add your current directory to the end of your path instead of the beginning, so you couldn't override commands in /bin /usr/bin ....

All of that said I don't add the current directory to my path.  I keep a ~/bin where I put my own scripts and program, I also keep a ~/bin32 and ~/bin64 where I put more updated versions of things I can find in /bin or /usr/bin or /usr/local/bin or ....  And I run the which and type commands frequently.

I can see where I should add the current directory to the end, as like you said, it would allow access to system commands over a possible same-named command in the current directory.

You also have some good ideas for naming script and bin directories in your home.

Thanks for your input and I apologize for letting the thread go a month before getting back to it!

---

