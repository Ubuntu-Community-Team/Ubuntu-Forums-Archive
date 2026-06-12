---
title: "Creating a custom command name to run another command."
date: 2009-10-26
forum: General Help
---

### Post by voncloft on 2009-10-26
I know the title sounds confusing here is what I want to do.  I want to run the command "/etc/init.d/samba restart" and save it to a command such as "restartserver" to run the command.  So instead of having to type out the entire command I can type one word.  Thanks in advance.

---

### Post by diesch on 2009-10-26
Add something like

```
alias restartserver="/etc/init.d/samba restart"
```

to your ~/.bashrc

---

### Post by undecim on 2009-10-26
> **diesch said:**
> Add something like

```
alias restartserver="/etc/init.d/samba restart"
```to your ~/.bashrc
After that, make sure to restart your terminal or type ```
. .bashrc
```
I would also like to point out the "service" command:```
service samba restart
```

---

### Post by iMisspell on 2009-10-26
If you dont want to cludder up your .bashrc file you can do the following.

Edit your .bashrc (find and uncomment - towards the bottom)
> if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

create your .bash_aliases file (in same dir as your .bashrc file)
and then put your alias hook's in there
```
alias restartserver="/etc/init.d/samba restart"
```

Boy are those alias a nice time sever and eazy on a person who has a bad-memory :P

Heres one you might like...
```
alias aledit='gedit $HOME/.bash_aliases'
```

Like said above, after you edit your .bash_aliases, you will need to open a new terminal window to take advantage of the edits.


[edit]
You could also add one of these...
```
alias alre='. $HOME/.bash_aliases; echo ".bash_aliases was reloaded"'
```
or
```
alias alre='echo "reloaded bash"; exec bash'
```

While playing with them i came up with "odd" (??) results.
The first will load new or edited alias hooks, but if you delete an alias line, it will still be active and usable.

The second will "clear" any deleted alias hooks along with load new or edited ones.

Maybe its my machine, i was just trying a bunch of different commands and maybe i clogged something up.



_

---

### Post by voncloft on 2009-10-27
> **iMisspell said:**
> If you dont want to cludder up your .bashrc file you can do the following.

Edit your .bashrc (find and uncomment - towards the bottom)


create your .bash_aliases file (in same dir as your .bashrc file)
and then put your alias hook's in there
```
alias restartserver="/etc/init.d/samba restart"
```

Boy are those alias a nice time sever and eazy on a person who has a bad-memory :P

Heres one you might like...
```
alias aledit='gedit $HOME/.bash_aliases'
```

Like said above, after you edit your .bash_aliases, you will need to open a new terminal window to take advantage of the edits.


[edit]
You could also add one of these...
```
alias alre='. $HOME/.bash_aliases; echo ".bash_aliases was reloaded"'
```
or
```
alias alre='echo "reloaded bash"; exec bash'
```

While playing with them i came up with "odd" (??) results.
The first will load new or edited alias hooks, but if you delete an alias line, it will still be active and usable.

The second will "clear" any deleted alias hooks along with load new or edited ones.

Maybe its my machine, i was just trying a bunch of different commands and maybe i clogged something up.



_

:D This definitely makes it easier to restart my server, thanks for the input.

---

### Post by iMisspell on 2009-10-27
> **voncloft said:**
> :D This definitely makes it easier to restart my server, thanks for the input.
Your welcome...
 


> **undecim said:**
> ..I would also like to point out the "service" command:```
service samba restart
```
Is there a difference between that and */etc/init.d/app restart* ?
Do some service's like it one way or another ?

Sorry to side track thread.

_

---

### Post by geirha on 2009-10-27
service is just a wrapper around init-scripts in /etc/init.d/. «service samba restart» will run «/etc/init.d/samba restart», so it just makes it a little prettier on the command-line. One useful thing though, is that you can do: ```
service --status-all
``` service is only in Intrepid and newer (if I remember correctly).

---

