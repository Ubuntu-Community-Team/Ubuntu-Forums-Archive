---
title: "xdg-open and run-mailcap: loop"
date: 2011-02-26
forum: General Help
---

### Post by sfresta on 2011-02-26
Hello guys,

several days ago I set up Firefox on KDE (using Kubuntu 10.04) to open any file using xdg-open, which opens files with the default application associated with the mime-type. To do this, I used a script written in ruby by a guy ([http://luisfpg.blogspot.com/2009/04/making-firefox-open-files-honoring-kdes.html](http://luisfpg.blogspot.com/2009/04/making-firefox-open-files-honoring-kdes.html)), that reads /etc/mime.types and generates the $HOME/.mailcap file used by run-mailcap.

After a nice apt-get upgrade, everything has stopped working. Each time you run xdg-open, it triggers a loop:

[B]xdg-open calls run-mailcap
run-mailcap calls xdg-ope[/B]n

I verified this by doing a simple test:

**$ xdg-open "Totale.pdf"**

I see from ps aux: "run-mailcap - action = view - debug Totale.pdf"

then:

**$ run-mailcap --action=view --debug Totale.pdf**
 - parsing parameter "Totale.pdf"
 - Reading mime.types file "/etc/mime.types"...
 - extension "pdf" maps to mime-type "application/pdf"
 - Reading mailcap file "/home/drosophila/.mailcap"...
 - Reading mailcap file "/etc/mailcap"...
Processing file "Totale.pdf" of type "application/pdf" (encoding=none)...
 - checking mailcap entry "application/pdf; xdg-open '%s';"
 - program to execute: xdg-open '%s'
 - **executing: xdg-open 'Totale.pdf'  <----- LOOP**

This loop is comparable to a fork bomb, **I have to reboot the system manually**. How to solve?


**$ cat .mailcap | grep pdf**
application/pdf; xdg-open '%s';

[B]
$ cat /etc/mailcap | grep pdf[/B]
application/pdf;        okular '%s';        nametemplate=%s.pdf;
test=test "$DISPLAY" != ""

---

### Post by sfresta on 2011-02-26
Solved.

The problem is the following:

Firefox reads $ENV{HOME}/.mailcap and executes the associated application (xdg-open in this case, but now you can set run-mailcap).

Xdg-open executes in a generic environment (new KDE etc..) the open_generic() function that executes run-mailcap:

> 

open_generic()
{
    # If it's a path or a file:/// URL, we can open it with run-mailcap
    if which run-mailcap >/dev/null &&
        (echo "$1" | grep -q '^file:///' ||
            ! echo "$1" | egrep -q '^[a-zA-Z+\.\-]+:'); then

        local file
        file="$1"

        # Decode URLs
        if echo "$file" | grep -q '^file:///'; then
            file=${file#file://}
            file=$(echo "$file" | perl -pe 's/%(..)/pack("c", hex($1))/eg')
        fi

        **run-mailcap --action=view "$file"**

        .....



Run-mailcap reads from **"$ENV{HOME}/.mailcap:/etc/mailcap:/usr/local/etc/mailcap:/usr/share/etc/mailcap:/usr/etc/mailcap"**

The only way to execute applications using the previous private mailcap file with Firefox without loop is the following:

1 - Rename your ~/.mailcap file in ~/.mailcap_firefox
2 - Open firefox
3 - about:config
4 - Search for: helpers.private_mailcap_file
5 - change the value in: ~/.mailcap_firefox

---

### Post by sfresta on 2011-02-26
Another solution for KDE:

If you don't want to rename the .mailcap file, you must not remove Konqueror. In this case, xdg-open will executes kfmclients insted of run-mailcap, without loop.

---

