---
title: "How to display message to, and accept input from, user"
date: 2010-07-04
forum: General Help
---

### Post by Ralph L on 2010-07-04
I am using LuckyBackup to back up my laptop disk to a USB disk.  I would like to display to the user the message "Please mount backup disk" and have the user click "OK".  LuckyBackup has a feature to allow issuing commands before it does the backup.  I have been investigating scripts (I have never written one.), but do not understand how to use them to this end.

Any help appreciated.

Ralph

---

### Post by bodhi.zazen on 2010-07-04
Try zenity:

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by Ralph L on 2010-07-05
bodhi.zazen

Thank you for your help.  Zenity seemed to work ok except the --question option asks a "yes or no" question, not a "cancel or ok" response to a request such as "Please mount the backup disk".  Do you know a way to get this response?

Anyway, Thank you very much for your help.

Ralph

---

### Post by Darkness Des on 2010-07-05
There's a way to test that.
```

zenity --stuph --moar_options --text="Please mount the backup disk".
# If the person said cancel, then tell them. If they said ok, then tell them that.
if [ "$?" == "1" ]; then
    echo "You clicked cancel."
elif [ "$?" == "0" ]; then
    echo "You clicked OK."
else echo "How'd you do that? You only had two options."
fi

```
The Man page on Zenity gives tons of examples, that's how I learned to use it. My BASH skills in general came from linuxcommand.org, which is my favorite manual on BASH ever.

---

### Post by Ralph L on 2010-07-05
Darkness Des

Thanks a lot for responding.  I really appreciate it.  However, I must be using an old version of zenity, since it doesn't support --stuph or --moar_options.  My zenity is 2.30.0-0.  Is there a new version available for Lucid that would include those options.

Thanks again

Ralph

---

