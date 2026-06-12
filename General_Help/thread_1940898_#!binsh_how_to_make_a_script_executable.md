---
title: "#!/bin/sh how to make a script executable"
date: 2012-03-14
forum: General Help
---

### Post by markMDW on 2012-03-14
I have a nonspecific linux program.  It installed under /usr/local/TheProgramFolder/ (owned by root)  

There is a script file that I can view but not execute; it has the header #!/bin/sh

There is an exec command in the script that runs the linux program:
exec /usr/lib/jvm/java-6-openjdk/jre/bin/java -cp .:lib/swing-worker-..... [it's very very long]

I have to navigate to the /usr/local/TheProgramFolder/ and copy and past this command into bash and the program runs [it won't run if I paste it into bash shell from my home folder.

How do I adjust the PATH file (where is it?) so that I can execute this anywhere and also how do I make the script file executable.  It's apparently already executable, but only as root.

Thanks for your time! Mark

---

### Post by matt_symes on 2012-03-14
Hi

Add it to .bashrc

```
export $PATH=$PATH:/usr/local/TheProgramFolder/:/the/next/path/ >> ~/.bashrc
```

Or edit /etc/enironment for global access. You also can to it to bash_profile if needs be. You may have to create that file.

Look at chown to allow you to run it from anywhere as it sounds like root is the owner.

```
sudo chown user:user /path/to/script
```

Where user is your user name.

You may just want to keep things like this in ~/bin though and add that to the _end_ of your $PATH. Otherwise it's a security risk (all be it a small one).

Kind regards

---

### Post by markMDW on 2012-03-14
As you suggested, I changed the ownership of the script file from root to my user name and group.  I have a launcher on my Desktop with the scipt file and path in quotations.  It now works.  Thanks very much for the expert help!

Mark

---

