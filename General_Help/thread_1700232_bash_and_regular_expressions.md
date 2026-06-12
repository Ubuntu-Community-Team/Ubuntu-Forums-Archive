---
title: "bash and regular expressions"
date: 2011-03-04
forum: General Help
---

### Post by ianc1 on 2011-03-04
I'm trying out my first bash script and I thought I'd start by testing a script to automatically added the repositories I use when I next do a fresh install.

I have a list of repositories called REPOS "name_ppa:repository/ppa name__ppa:repository/ppa" etc

Now my script uses```
echo ${name%%'_'*}
```to pick out the name before the '_' and prompt for an add yes/no.  On yes it runs ```
sudo add-apt-repository ${name##*'_'}
```which picks the bit after the '_'.

Now my question is really simply, I think I am using gedit and the echo command is in a purple colour and the ${name in a blue colour the ##, %% and * are in black '_' are in the same colour as comments but unlike the opening { the closing } is in the same colour as the echo.  I don't understand this colouring. ie why are the opening and closing curly braces not the same colour?

---

