---
title: "automate searches"
date: 2009-11-15
forum: General Help
---

### Post by 1in0 on 2009-11-15
His,
 
I want to be able to:
 
1) copy some selected text (Ctrl + C will do [IMG]http://www.linuxforums.org/forum/images/smilies/icon_wink.gif[/IMG]
2) filter out some characters of the selected text into some string (also not difficult with bash)
3) and finally search this string inside text files in some directory. Preferably i want a nice and convenient visual application like "find in files" given by some editors, searchmonkey or even some indexing search apps like tracker or beagle
 
i really use this procedure a lot and i wish i could automate it like in windows with autohotkey
 
until now i tried automation tools like xnee, xautomation or xmacro, but i have problems with the installation and/or usage...
 
searchmonkey, for one, doesn't accept command line options for searching - that would be perfect for automating the procedure since all i'd need would be some little script and a keyboard shortcut...
 
i'm also thinking of going bash all the way since i already installed xclip to read the content of the clipboard; and the searching, even though a text based one, could be tailored almost to my needs...
 
but before i waste more time:
 
-> does anyone know or has any ideas on how to do this?!
 
thanks!

---

### Post by 1in0 on 2009-11-16
here is a quick hack inspired by medit and using bash, the gnome-terminal and gnome keyboard shortcuts (note that i don't know how it all works. or even if it works 100%):

bash script, lets call it fif (Find In Files):
```

#!/bin/bash

if [ -z "$1" ]; then
# search clipboard
  search=`xclip -o -selection=clipboard -display="localhost:0"`
# Clean search string to use only alphanumeric characters:
  search=`echo -ne "$search" | tr -cs '[a-z][A-Z][0-9]' '.'` # This converts all non-alphanumeric #characters to dots, then squeezes each string of repeated dots into a single dot
else
  search=$1
fi

if [ -z "$search" ]; then
echo $search
  echo "Nothing to search!"
  read -n1
  exit 1
fi

if [ "${#search}" -lt "3" ]; then
echo $search
  echo "Search term is shorter than 2 characters ..." # Better dumdum filtering needed here :)))
  echo -n "Continue? (Y/n)"
  read keyin
  if [ ! "$keyin" = "Y" ]; then
    exit 0
  fi
fi

sdir='~/CD-LIST'
cd $sdir

echo -e "Searching '$sdir' for \033[1m$search\033[0m:"

find . -type f \( -iname "*.txt" -o -iname "*.csv" \) -print -follow | sed -e "s/ /\\\ /g" -e "s/'/\\\'/g" | xargs egrep -I -s -H -n -i -e "$search" > ~/bin/gsearch.txt

cat ~/bin/gsearch.txt| sed 's/.txt:/.txt:\n\tL:/g' | sed 's/.csv:/.csv:\n\tL:/g' | uniq -u
# arrange output: separate file and hit lines # BUG: "TXT", "CSV" and variants aren't seen..

echo "*** `cat ~/bin/gsearch.txt | wc -l` matches found ***"

echo -ne "\033[1mDone\033[0m searching '$sdir' for \033[1m$search\033[0m."
echo    " Use Shift+ Up, Down, Begin, End keys to navigate. Ctrl+ +/- to zoom in/out."

echo -ne "\033[47m\033[30m-> Press any key to quit terminal\033[0m" # echo only if inside a terminal window called SEARCH...
read -n1 # read one character

```now create a new shortcut called fif (or whatever) with the command:

```

$ gnome-terminal --window-with-profile=search --command="fif" --geometry 200x100 --maximize  --zoom=1.0&

```btw, i created a new gnome-terminal profile to my liking called "search"

and that's it :D
a terminal based search of my "database" in ~/CD-LIST

some graphical/mouse automation should follow... eventually ... :)

What do you think? and how do you do these things yourselves...?

---

