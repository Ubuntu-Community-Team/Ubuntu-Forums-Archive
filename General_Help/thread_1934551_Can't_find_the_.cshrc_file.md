---
title: "Can't find the .cshrc file"
date: 2012-03-02
forum: General Help
---

### Post by ChemMeister on 2012-03-02
I don't see the '.cshrc' file in the 'etc' folder, i need to edit it, so that some commands are executed when i open a C shell. Any ideas? Thanks

---

### Post by aeiah on 2012-03-02
i think usually best practice is to have your .cshrc file in your home directory rather than rely on the system one. the filename starts with a dot, so it is hidden. have you shown hidden files?

it isn't at /etc/.cshrc on my system (debian). if it isn't there you can just create it yourself (or create it in your home directory)

---

### Post by ptn107 on 2012-03-02
```
sudo touch ./.cshrc && sudo gedit ./.cshrc
```

---

### Post by Khayyam on 2012-03-02
> **ptn107 said:**
> ```
sudo touch /etc/.cshrc && sudo gedit /etc/.cshrc
```

No, there are no 'dotfiles' in /etc .. it won't be read by csh as it expects to find /etc/cshrc. As aeiah stated create a .cshrc in $HOME and it'll be read at startup.

Please be more careful about the kind of advice you offer.

best ... khay

---

