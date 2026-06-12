---
title: "program that shows custom quotes at startup?"
date: 2010-06-02
forum: General Help
---

### Post by Andrew Golightly on 2010-06-02
What's a good program that shows quotes at startup? Quotes that I could edit and add to? thanks!

---

### Post by BenAshton24 on 2010-06-02
I don't know of such a program but here's one in python... It's ugly code but it works :)

***quotes.py***
```
#!/usr/bin/env python
import gtk, pygtk, os, sys
from random import randint
os.chdir(sys.path[0])
q = open('./quotes.txt')
quotes = q.readlines()
q.close()
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_CLOSE, quotes[randint(0, len(quotes)-1)])
md.set_title("Quote of The Day")
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()
```

***quotes.txt***
```
The grass isn't always greener on the other side
Don't cry over spilled milk
Another quote of some sort
```

Just add it to your startup applications and edit quotes.txt with all of your quotes. (quotes.txt must be in the same folder as the script)

Hope this helps...
Ben.

---

### Post by inameiname on 2010-06-02
This is cool. I just may have to try this out.

Seems like you can put whatever you want in the 'quotes.txt'. Could make a few different ones.

---

### Post by wyliecoyoteuk on 2010-06-02
What you need is a MOTD (message of the day) or a "fortune cookie" program.
fortune is in the repos, along with a 1500 cookie database.

---

### Post by inameiname on 2010-06-02
I've never heard of the fortune cookie program. Cool.

Oh, and fyi, it's fortune-mod when you install it:

sudo apt-get install fortune-mod

And you can read a new fortune every time you write "fortune" in the terminal.

---

### Post by Andrew Golightly on 2010-06-05
Thanks Ben. I was thinking about the time I wanted this, that maybe I'd learn how to program in Python. This was a great way to get into it. To create more flexibility with quotes, I created a directory where any file can be added. The way it's setup, I can have multiline quotes too.
```

#!/usr/bin/env python
import gtk, os
from random import randint

# Read in the filenames of the quotes
quote_files = os.listdir('quotes')

# and choose one of them randomly
quote_file = open('quotes/' + quote_files[randint(0, len(quote_files)-1)])
# Read it's contents and close the file
quote = quote_file.read()
quote_file.close()

# Setup and display the dialog with the contents of the quote
md = gtk.MessageDialog(None, gtk.DIALOG_DESTROY_WITH_PARENT, gtk.MESSAGE_INFO, gtk.BUTTONS_OK, quote)
md.set_title("Quote of the day")
#md.set_size_request(333) # look at displaying a minimum width so the title always shows
md.set_position(gtk.WIN_POS_CENTER)
md.run()
md.destroy()
```

I'm just looking at working out later how to set a minimum dialog box width so that the title always shows fully. If the quote is too small, sometimes only half the title will show.

Thanks for starting me off Ben!

---

### Post by Andrew Golightly on 2010-06-08
Something happened. It was all working fine...

And now when I login I don't see the dialog box anymore. It runs fine when I run it manually... any idea why it's not working as a startup program? It's in the startup program list..

:rolleyes:

---

