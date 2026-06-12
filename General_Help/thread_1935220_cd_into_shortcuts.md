---
title: "cd into shortcuts"
date: 2012-03-03
forum: General Help
---

### Post by Sachin_ruk on 2012-03-03
Hi all,

So I have created a shortcut called thesis on my (dont know the proper name) folder explorer. I want to cd into this without actually typing in the long folder path into it in the terminal.

i.e. can I do:
cd thesis
as opposed to cd ~/home/long/directory/path/thesis

Thanks,
Sachin

---

### Post by HavarN on 2012-03-03
if you add a line to your ~/.bashrc like this:```
alias goto-thesis=cd ~/home/long/directory/path/thesis
```Swith ~/home/long/directory/path/thesis with the actual path.

Then you can just type goto-thesis in the terminal to go there. (You have to close and reopen the terminal after having added that line to $HOME/.bashrc).

---

### Post by Khayyam on 2012-03-03
Sachin ...

I don't know that bash supports this but with zsh I can cd deep into a directory tree like so:

```
% mkdir -p long/directory/path/thesis
% cd */**/thesis
```

The problem with an alias is that it actually doesn't save that much typing.

```
% cd l<tab>d<tab>p<tab>t<tab>
```

There are also other methods of shortening the path, we could use 'ln' to make a (symbolic) link (which is as reusable as an alias).

```
% ln -s long/directory/path/thesis thesis
% cd thesis
```

best ... khay

---

### Post by hwttdz on 2012-03-03
+1 for linking.

---

### Post by nd456 on 2012-03-03
> **Sachin_ruk said:**
> Hi all,

So I have created a shortcut called thesis on my (dont know the proper name) folder explorer. I want to cd into this without actually typing in the long folder path into it in the terminal.

i.e. can I do:
cd thesis
as opposed to cd ~/home/long/directory/path/thesis

Thanks,
Sachin
The folder explorer is Nautilus

---

