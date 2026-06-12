---
title: "Need some basic CLI help"
date: 2011-05-14
forum: General Help
---

### Post by Keypel on 2011-05-14
```
apt-get install build-essential asciidoc binutils bzip2 gawk gettext \
  git libncurses5-dev libz-dev patch unzip zlib1g-dev
```

I having a hard time with this command. I tried pasting the whole command into a terminal but got an error. Sorry, I forgot what the error was.

Then, I tried pasting in just the first line

[COLOR="Blue"]apt-get install build-essential asciidoc binutils bzip2 gawk gettext[/COLOR]

This time I got a permission error so I added sudo and got that part to install.

Now I am having a hard time with the second part:

[COLOR="#0000ff"]git libncurses5-dev libz-dev patch unzip zlib1g-dev[/COLOR]

The error I get now is:

```
user-01@PC-01:~$ git libncurses5-dev libz-dev patch unzip zlib1g-dev
git: 'libncurses5-dev' is not a git command. See 'git --help'.
user-01@PC-01:~$
```

Can somebody please explain to me what my mistakes are? I'm tryng real hard to understand this CLI stuff.

---

### Post by jocko on 2011-05-14
the \ at the end of the first line means the next line is part of the same command. So it should have been:
```
sudo apt-get install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch unzip zlib1g-dev
```
But since you've already installed some of the packages, this will do it for you:
```
sudo apt-get install git libncurses5-dev libz-dev patch unzip zlib1g-dev
```

---

### Post by Keypel on 2011-05-14
> **jocko said:**
> the \ at the end of the first line means the next line is part of the same command. So it should have been:
```
sudo apt-get install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch unzip zlib1g-dev
```
But since you've already installed some of the packages, this will do it for you:
```
sudo apt-get install git libncurses5-dev libz-dev patch unzip zlib1g-dev
```

Thank you very much.

---

