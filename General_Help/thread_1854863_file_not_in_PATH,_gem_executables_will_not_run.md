---
title: "file not in PATH, gem executables will not run"
date: 2011-10-05
forum: General Help
---

### Post by giac0m0 on 2011-10-05
Hello, I am having issues installing Ruby Gems.  On a stock 11.04 Ubuntu I ran the following commands to prep my installation:

```

$ sudo apt-get install libcurl3 libcurl3-dev
$ sudo apt-get install rubygems
```Ubuntu worked out the correct curl and ruby for my install and installed it.

The problem happens when I try to install any gem, I get the following error:

```

$ sudo gem install --user-install [gem_name]

``````

WARNING: You don't have /home/giac0m0/.gem/ruby/1.8/bin in your PATH,
                 Gem executables will not run.
Sucessufully installed [gem_name]

```So, I have tried:

```

$ export PATH=/home/giac0m0/.gem/ruby/1.8/bin:$PATH

```and using the instructions from Taurus on this thread:
[http://ubuntuforums.org/showpost.php?p=6268914&postcount=2](http://ubuntuforums.org/showpost.php?p=6268914&postcount=2)

editing the .bashrc file to add the line (at the bottom of the file):

```

PATH=$PATH:/home/giac0m0/.gem/ruby/1.8/bin
export PATH

```and run the script with:

```

source ~/.bashrc

```I get no confirmation that I have updated my path and even after a power cycle I still get the gem errors when trying to install the gems.  Any thoughts?

---

### Post by giac0m0 on 2011-10-14
*bump*

---

