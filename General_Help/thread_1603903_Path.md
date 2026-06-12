---
title: "Path ?"
date: 2010-10-23
forum: General Help
---

### Post by hantechbl on 2010-10-23
I need to know how to install Python 2.6 on Ubuntu 8.04, I checked and the latest ver. on the ubuntu repository is 2.5 I need 2.6 I just compiled it using the following guide..[http://www.saltycrane.com/blog/2008/10/installing-python-26-source-ubuntu-hardy/]("http://www.saltycrane.com/blog/2008/10/installing-python-26-source-ubuntu-hardy/") I just didn't get how to set my PATH I followed all the steps that were there exactly.  Any help would be appreciated :)

---

### Post by gmargo on 2010-10-23
There's a good example of how to augment your $PATH right in the default $HOME/.profile file.  It adds $HOME/bin to the path.  So add a similar section for python to your $HOME/.profile (adjust for correct path to the bin directory):

```

# set PATH so it includes user's private python bin directory
if [ -d "$HOME/lib/python2.6/bin" ] ; then
    PATH="$HOME/lib/python2.6/bin:$PATH"
fi

```

---

### Post by yetiman64 on 2010-10-23
**Or** in the same file (.profile) gmargo mentions you could use the export command (if adjusting a script doesn't suit you), eg add the line,

> export PATH=$PATH:</Add/your/python_folder/path/here> replace  </Add/your/python_folder/path/here> with the path of your python folder.

An example (from the guide you linked to) would look like,
> export PATH=$PATH:$HOME/lib/python/bin/python2.6Then log out of your desktop and log back in and check it is correct with,

```
echo $PATH
```Your python folder should now be at the end of the output. 

**To place it at the start** you can just swap "$PATH" and "$HOME/lib/python/bin/python2.6" around, though don't move the full colon from between them. 

Only real advantage of this method is it is only 1 line to add.

---

