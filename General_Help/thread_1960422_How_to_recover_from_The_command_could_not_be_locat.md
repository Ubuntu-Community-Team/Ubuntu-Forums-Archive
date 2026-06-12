---
title: "How to recover from The command could not be located because '/usr/bin' is not includ"
date: 2012-04-17
forum: General Help
---

### Post by antoaravinth on 2012-04-17
Hi all,

I added these lines to my `.bashrc` file:

    ```
export vertx_home=/anto/vertx/bin
    export PATH=${PATH}:${vertx_home}/bin
```

after doing that. I get an error message like that for all command's I run, for example:`clear`,`groovy` :

    ```
Command 'clear' is available in '/usr/bin/clear'
    The command could not be located because '/usr/bin' is not included in the PATH environment variable.
    clear: command not found
```

How to recover from it? I couldn't able to open anything via terminal :( 

I did :

```
echo $PATH 
```

which prints:

```
${PATH}:${VERTX_HOME}

```

I'm very new to Ubuntu. I'm using Ubuntu 10.10. Now what I need is to know where that .bashrc file resides as I can go there manually and change it. Kindly help.

Thanks in advance.

---

### Post by lukeiamyourfather on 2012-04-17
This is what you were probably wanting to do.

```

PATH=$PATH:/anto/vertx/bin

```

Since your path is all jacked up either use a different user to modify the files or call a text editor directly with the full path to it.

---

