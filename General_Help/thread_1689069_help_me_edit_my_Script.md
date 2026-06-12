---
title: "help me edit my Script"
date: 2011-02-16
forum: General Help
---

### Post by haris2887 on 2011-02-16
hello all i have a script which enables suspent on my laptop, it works very well..
now i want to add to the script so everytime i suspend or hibernate it
issues pkill -f docky command (to kill the dock and then suspend)

upon resume it should start Docky

here is the script i wish to edit.
> #!/bin/sh

TMPLIST_E=/tmp/ehci-dev-list
TMPLIST_X=/tmp/xhci-dev-list
E_DIR=/sys/bus/pci/drivers/ehci_hcd
X_DIR=/sys/bus/pci/drivers/xhci_hcd
E_BIND=$E_DIR""/bind
E_UNBIND=$E_DIR""/unbind
X_BIND=$X_DIR""/bind
X_UNBIND=$X_DIR""/unbind


#param1 = temp file, param2 = device dir, param3 = unbind 
unbindDev (){
#inspired by [http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19](http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19)    
  echo -n '' > $1
    for i in `ls $2 | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
      echo -n "$i" | tee $3
      echo "$i" >> $1
  done
}

#param1 = tem file, param2 = bind
bindDev(){
  [ -f $1 ] || return
  
  for i in `cat $1`; do
    echo -n "$i" | tee $2

  done
  rm $1
}


case "${1}" in
  hibernate|suspend)
    unbindDev $TMPLIST_E $E_DIR $E_UNBIND
    unbindDev $TMPLIST_X $X_DIR $X_UNBIND
        ;;
  resume|thaw)
    bindDev $TMPLIST_E $E_BIND
    bindDev $TMPLIST_X $X_BIND
        ;;
esac

---

### Post by tredegar on 2011-02-16
Maybe change this part (leave the rest as it is)
```
case "${1}" in
hibernate|suspend)
[COLOR="Red"]pkill -f docky[/COLOR]
unbindDev $TMPLIST_E $E_DIR $E_UNBIND
unbindDev $TMPLIST_X $X_DIR $X_UNBIND
;;
resume|thaw)

bindDev $TMPLIST_E $E_BIND
bindDev $TMPLIST_X $X_BIND
[COLOR="Red"]docky &[/COLOR]
;;
esac 
```

Edit
Except, if that file is being run as root, this isn't the way to do it, as root won't know about your GUI, the kill will probably work, but not the restart of docky.
/Edit

---

### Post by haris2887 on 2011-02-16
yes it is being run as root
any other ideas

you were right it kill fine but wont restart docky

---

### Post by tredegar on 2011-02-16
Time to start a new thread I think, because I do not know the answer, and people are going to see your "Help me edit my script" title, see it has been replied to, and probably move on.

Maybe title it something like :
> "How can a root script start a GUI application on my desktop?"

I am having trouble with resume from hibernate or suspend.

I am trying to get a script that is run by root to restart docky on my desktop (see this thread [put link] for the details)

How can a root process start *any* application in my GUI?

It would be sensible to reference this thread so people know what you are trying to do, and why.

Good luck.

---

