---
title: "Disable tabs in gedit?"
date: 2010-12-19
forum: General Help
---

### Post by viktorzk on 2010-12-19
Hello,
Can I disable the tabs in gedit? I want it to behave like notepad in Windows.
I found instructions for adding 'open in new window' menu options, but I want whenever I doubleclick on a text file or run 'gedit filename', the file to be opened in a separate window.
Thanks!

---

### Post by viktorzk on 2011-01-01
bump

---

### Post by AlphaLexman on 2011-01-01
I don't think you can get rid of the tabs, but
```
gedit --new-window filename.txt
```
will open in a new window instead of a new tab...

or,

just drag and drop the desired tab to an empty area on the desktop, and it will open a new window.

---

### Post by mc4man on 2011-01-01
If you want this always (as a user), the you could open edit menus - accessories - then r. click on 'text editor' - properties

Edit the command to include the above posted, ie.
gedit --new-window %U

or create a custom definition thru the open with - other application - use a custom command
(if you are using maverick and leave the 'Remember this....' option enabled then the custom will become the new default 
The custom def. - can be found in ~/.local/share/applications as 
userapp-gedit-XXXXXX.desktop
If you open it in a text editor you can give it a distinctive name if desired

---

### Post by viktorzk on 2011-01-02
Thank you for the replies!

mc4man, that works well. The only downside that I see is that I have to type out '--new-window' whenever I want to open gedit from alt+f2, which I do a lot.

I tried another solution: renaming the gedit application to gedit_old, and creating a new one with the following code:

```
#include <cstdlib>
#include <cstring>
using namespace std;
int main(int argc,char*argv[])
{
    char cmd[1000]="gedit_old --new-window ";
    for(int i=1;i<argc;i++)
        {strcat(cmd,"\"");strcat(cmd,argv[i]);strcat(cmd,"\" ");};
    strcat(cmd,"&");
    system(cmd);
    return 0;
}
```It seems to work flawlessly so far. Can you think of any disadvantages of this solution? Or any file path/options that will break it?

---

### Post by mc4man on 2011-01-02
^ will have to give that way  a try. (always interested in different approaches

One of the best things about linux is how it can be multipath.
I also prefer separate windows, particularly when editing source code or manually apply patches, ect.

For the r.click, which I use most, ended up editing the /usr/share/applications/gedit.desktop
For terminal use -  used an alias in ~/.bashrc
So there appears to be several ways to skin the cat.

---

