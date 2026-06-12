---
title: "python-optcomplete not working"
date: 2010-11-21
forum: General Help
---

### Post by nasp on 2010-11-21
Hi everyone.

I'm running on an Ubuntu 10.10 fresh install and I'm having trouble with python-optcomplete. First of all i have the bash-completion and python-optcomplete package installed correctly. I'm running python 2.6.6.

Here's the content of my /etc/bash_completion.d/optcomplete:
```
_optcomplete()
{
    COMPREPLY=( $( \
        COMP_LINE=$COMP_LINE  COMP_POINT=$COMP_POINT \
        COMP_WORDS="${COMP_WORDS[*]}"  COMP_CWORD=$COMP_CWORD \
        OPTPARSE_AUTO_COMPLETE=1 $1 ) )
}
```

And i have /usr/lib/python2.6/dist-packages/optcomplete.py installed correctly.

Now when i run [[COLOR="Blue"]_this file as test.py_[/COLOR]]("http://pastie.org/1314648") i don't get completion!

For example if i do:
```
/$ python test.py -
```
I get
```
-   -c  -d  -E  -h  -i  -O  -Q  -S  -t  -U  -u  -V  -v  -W  -x
```
Which is non-sense.

The same happen when i do:
```
/$ python test.py fo
```
I get no completion at all.
But i should get
```
/$ python test.py foo
```

Is there so kind of log where i can get an error atleast?

I recently installed virtualenv but I don't think it worked before. Plus I have another machine running 10.10 which works perfectly.

Thanks
Simon

---

