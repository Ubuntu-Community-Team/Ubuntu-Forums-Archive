---
title: "mv file to directory that has not been created yet"
date: 2010-02-10
forum: General Help
---

### Post by bwitherell on 2010-02-10
Hi,

is there a way i can use mv or another command to move a file to a directory that has not been created yet.

Id like to be able to create the directory and move the file in one command. Can this be done? if so how?

Any help is appreciated.

Thanks.

---

### Post by Richard1979 on 2010-02-10
touch DIRECTORY/; mv FILE DIRECTORY/

The semicolon is your friend.

---

### Post by bwitherell on 2010-02-10
> **Richard1979 said:**
> touch DIRECTORY/; mv FILE DIRECTORY/

The semicolon is your friend.

Thanks for the help. i do need a way though that i could get it to only try to create the directory if it does not exist.

thanks.

---

### Post by Richard1979 on 2010-02-10
Maybe use "mkdir":

Note the error code though:
```
root@lara:/tmp# mkdir /tmp/testing
root@lara:/tmp# mkdir /tmp/testing
mkdir: cannot create directory `/tmp/testing': File exists

```Other than that, try PHP CLI:

```

<?php

if (!shell_exec('mkdir DIRECTORY')) {
    shell_exec('cd DIRECTORY; touch FILE;');
} else {
    shell_exec('mkdir DIRECTORY; cd DIRECTORY; touch FILE;');
}
?>

```

Save the file as something.php and execute it as:
```

php something.php
```

(not tested but should work)

---

### Post by kaibob on 2010-02-10
> **bwitherell said:**
> Thanks for the help. i do need a way though that i could get it to only try to create the directory if it does not exist.

thanks.

You can use mkdir with the -p option. If the directory already exists, mkdir does nothing.

```
mkdir -p /target/directory ; mv file /target/directory
```

From the mkdir man page:

> -p, --parents
no error if existing, make parent directories as needed

---

### Post by bwitherell on 2010-02-11
> **kaibob said:**
> You can use mkdir with the -p option. If the directory already exists, mkdir does nothing.

```
mkdir -p /target/directory ; mv file /target/directory
```

From the mkdir man page:

Thanks, I probably should have read the man page for mkdir. I do not think im going to get a one command solution. even though this is one line it is still two commands. but ill have to just not be so lazy and just type the two commands.

Thanks for this. I think this is the solution i will use.

---

### Post by amac777 on 2010-02-11
If you'd like this to really be a one line command, you can easily make it as a script and put it somewhere in your path. For example,

```
sudo nano /bin/mv2
```

with this contents:

```
#!/bin/bash
mkdir -p "$2"
mv "$1" "$2"
```

and then make it exectuable:

```
sudo chmod +x /bin/mv2
```

Now you can use your new "mv2" command to move files to directories that don't exist by just typing this:

```
mv2 file directory-that-does-not-exist
```

---

### Post by bwitherell on 2010-02-11
> **amac777 said:**
> If you'd like this to really be a one line command, you can easily make it as a script and put it somewhere in your path. For example,

```
sudo nano /bin/mv2
```

with this contents:

```
#!/bin/bash
mkdir -p "$2"
mv "$1" "$2"
```

and then make it exectuable:

```
sudo chmod +x /bin/mv2
```

Now you can use your new "mv2" command to move files to directories that don't exist by just typing this:

```
mv2 file directory-that-does-not-exist
```


That's a great idea! thanks. This is definitely the method I'm going to use.

---

### Post by bwitherell on 2010-04-21
I created the mv2 script and it suits my needs well. Thank you.

---

