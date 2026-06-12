---
title: "ex/vim in shell scripts"
date: 2010-12-10
forum: General Help
---

### Post by Jay Hawk on 2010-12-10
Hi good people.
i am trying to make a bash script, that installs apache2 automatically.
the thing i need (and cant get working) is this:
I have a variable $wwwHomeDir="$HOME/devel/www"

and now i would like to change all "/var/www" to $wwwHomeDir in /etc/apache2/sites-available/default

i have tried to pipe to ex like this:

using the file ./default

this works:
echo -e "g/\/var\/www/ s//XXXXXX\nw\nq\n" | ex default

this fails:
echo -e "g/\/var\/www/ s//$wwwHomeDir\nw\nq\n" |  ex default

Why?
(i have tried to escape the slashes in the variable too)

best regards
/jesper

SOLVED
Did this instead:

wwwHomeDir="$HOME/devel/www"
echo -e "1,\$s:/var/www:$wwwHomeDir:\nw\nq\n" | sudo ex /etc/apache2/sites-available/default

---

