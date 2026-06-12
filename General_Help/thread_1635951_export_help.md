---
title: "export help"
date: 2010-12-02
forum: General Help
---

### Post by COKEDUDE on 2010-12-02
When you do something like the below command, where does it get exported to? I noticed it doesn't go to the .bashrc. 

```
export HISTTIMEFORMAT='%F %T '
```

---

### Post by Habitual on 2010-12-02
to the history command and is only effective while the c-li session is open. 
Add to .bashrc for permanence.

Output from "yours":
  753  2010-12-02 14:31:46 echo $HISTTIMEFORMAT
  754  2010-12-02 14:32:09 history

"Regular":
  744  sudo grub-install /dev/sda
  745  sudo update-grub
  746  history

Mine. :) (I remove the stamps using 'hist' to see it this way, else history it is)

alias hist='history | sed '\''s/^[ 0-9]* //'\'''
sudo grub-install /dev/sda
sudo update-grub
history

---

### Post by COKEDUDE on 2010-12-02
> **Habitual said:**
> to the history command and is only effective while the c-li session is open. 
Add to .bashrc for permanence.

Output from "yours":
  753  2010-12-02 14:31:46 echo $HISTTIMEFORMAT
  754  2010-12-02 14:32:09 history

"Regular":
  744  sudo grub-install /dev/sda
  745  sudo update-grub
  746  history

Mine. :) (I remove the stamps using 'hist' to see it this way, else history it is)

alias hist='history | sed '\''s/^[ 0-9]* //'\'''
sudo grub-install /dev/sda
sudo update-grub
history

What do you mean by "yours": and "Regular": ?

---

### Post by COKEDUDE on 2010-12-11
What do you mean by "yours": and "Regular": ?

---

### Post by Habitual on 2011-01-28
Yours vs default I should have said.

export HISTTIMEFORMAT='%F %T '
then
history

gives you this formatted output:
712  2011-01-28 19:46:55 export HISTTIMEFORMAT='%F %T '
713  2011-01-28 19:46:59 history

vs.

default (AFAIK)
714  export HISTTIMEFORMAT='%F %T '
715  history

---

