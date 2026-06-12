---
title: "Fonts - GTK"
date: 2012-03-15
forum: General Help
---

### Post by anewguy on 2012-03-15
I had another thread open on this but closed it as I wasn't quite getting the information I needed.  What I want to do:

- using GTK 3 and C
- give the user a different selection box for font, font size, font color and font attributes like bold and italics

What I have tried:

- gtk_font_button_new.  It provides all of this except color, except that bold and italics aren't separate, neither is the size.  I've the setting the style and size to false but all that does is hide them in the label on the screen, not in the selection dialog. It also requires that I use some things from Pango to extract what I need, and with as little as I know about GTK, I don't know squat about Pango.

- I tried gtk_font_chooser_dialog_new, but ran into problems.  First off, it appears just to be a front-end or different name for gtk_font_button_new.  Worse though, it bombs out at execution time saying I can set a parent on a window that is already a parent or some such thing.  Basically, I know this is because gtk_font_chooser_diaglog appears to want a gtk window to display the dialog in -> I gave it my current window name.

If you look at the top of the message window for submitting a thread or a response here, you'll see the "Fonts" font family selection, the "Size:" font size selection, the "A" for Font color, and underneath those are the bold, italics and underline toggles.  These are the functions I need to duplicate.

The program I am working on updates a CSS file (and nope, I don't know squat about CSS - just writing something to edit some values for someone).  I need the font name, size, color and "weights" to all be separate strings so I can work with them.

Any input would be greatly appreciated!!

Thanks in advance!
Dave ;)

---

### Post by anewguy on 2012-03-16
Please forgive the bump an hour early.  I'm going to be away until later this evening and was really hoping someone could provide me with some guidance on this.

Thanks in advance!
Dave ;)

---

### Post by anewguy on 2012-03-17
No answer?  Hummmmmm......

I hope (but find itquite hard to believe given the audience) that nobody has an answer.  If it's a personal thing, please just say so and why, as I thought this was a legitimate question in a forum I hoped worked the same as the other Ubuntu forums.

---

### Post by anewguy on 2012-03-18
I'm guessing this is dead.

---

### Post by anewguy on 2012-03-18
After a lot of searching an changing terms around for the search to exclude anything to do with pango, gtk, etc., I found the following.  Has anyone ever used this, and if so, is there a certain path I need to specify to get all the fonts?  Also, what the heck is, where do I get and how do I specify "Display"?  Are they asking about things like "Display 0" like we used to put in xorg.conf?  Can I put NULL in here and let it default? Or is this a variable returned by the function?

XListFonts()

Syntax
char **XListFonts(display, pattern, maxnames, actual_count_return)
      Display *display;
      char *pattern;
      int maxnames;
      int *actual_count_return;


Arguments
display  Specifies the connection to the X server.  
pattern  Specifies the null-terminated pattern string that can contain wildcard characters.  
maxnames  Specifies the maximum number of names to be returned.  
actual_count_return  Returns the actual number of font names.  


It says:  as controlled by the font search path; see XSetFontPath().


In addition, my C is rusty enough I don't remember what the double "*" means - is this a pointer to a pointer?

If you can help in anyway, PLEASE do so.

Thanks in advance.

Dave

---

### Post by nothingspecial on 2012-03-19
Let's try this question here for a while :)

Moved to General Help.

---

### Post by r-senior on 2012-03-19
I think you've got a Pango phobia, although after writing this, I think I might be getting it too! ;)

```
#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>

void list_available_fonts_for_widget(GtkWidget *w)
{
	PangoContext *context;
	PangoFontFamily **families;
	int i, n;
	
	context = gtk_widget_get_pango_context(w);
	pango_context_list_families(context, &families, &n);
	
	for (i = 0; i < n; i++) {
		puts(pango_font_family_get_name(families[i]));
	}
	
	g_free(families);
	g_object_unref(context);
}

int main( int argc, char *argv[])
{
	GtkWidget *window;

	gtk_init(&argc, &argv);
	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	list_available_fonts_for_widget(window);

	return EXIT_SUCCESS;
}
```

Assuming this snippet is in pango.c, compile with 

```
gcc -o pango pango.c `pkg-config --libs --cflags gtk+-3.0
```

I'd understand if you want to stick with C, but I do wonder if learning Python would be more productive in the long run. Here's the equivalent to the C above:

```
from gi.repository import Gtk, Pango

class MainWindow(Gtk.Window):

	def __init__(self):
		Gtk.Window.__init__(self)

	def list_available_fonts(self):
		context = self.get_pango_context()
		for family in context.list_families():
			print family.get_name()
		
window = MainWindow()
window.list_available_fonts()
```

EDIT: Assuming that goes into pango.py, you'd run that with ```
python pango.py
```

That said, is this going to be useful for your CSS editor anyway? The above list fonts for the system your program runs on, but the fonts for CSS won't be that set of fonts.

---

### Post by anewguy on 2012-03-19
Thank you for the reply!!

I'll do some extra explaining here for those who might be seeing this thread since it was moved for more visibility:

I would think in this case those fonts would work.  Even though it's a CSS file, it's not being used in a browser.  It is a theme "control" file for Gnome Shell - not Gnome as we install with Ubuntu, but the actual package Gnome Shell.  Once installed, it has a gnome-shell.css file it uses to define how things like the top bar, menu items, icons, etc., appear on the desktop.  Currently people are editing this by "hand" and putting in their own hex values for colors, etc..  Needless to say this leads to a lot of trial and error.  They have said no editor currently exists, so that's why I started this project.  Currently I'm just working with the most basic of configuration items in the panel definition section of that css file.  I've got color selection working, including making sure that you can only have 1 active background option (color, image or gradient currently).

So I moved on to the next one requested - fonts.  I thought generating a list of available fonts in a drop-down wouldn't be a problem.  I want the individual boxes like you see in so many programs - the font, the font size, the font color, bold, italic, etc..  Seems like it *should* be a simple enough request.

I do have the default GTK selection screen working - I just haven't figured out the pango stuff to parse it yet as we already talked about.  That's mainly because I really want these things separate.

I'm also attaching screen prints for those new to this thread.

r-senior - again I appreciate your help on this as you have been trying all along.  You went more than the extra mile to come up with the pango sample - it is GREATLT appreciated!  I'll give that a try a little later on when I have some time to concentrate on it - like trying to understand it and then putting it to use ;)  I can't say thank you enough, and in having these threads moved around, etc., it is meant as no reflection on the wonderful help you have been providing.  I was hoping I was just missing something extremely simple - like "gtk_list_fonts" or something ;)

Thanks again!

Dave ;)

---

### Post by anewguy on 2012-03-19
Jeez - now I've done the same thing 2 times in a row - forgot the screen shots!!  They are attached here.

Given the more info on what this is all about, if anyone knows of an existing tool that already does this (edits the gnome-shell.css file), has a better way to do it, etc., just let me know.  I don't know css, I don't know Gnome Shell, I barely get by in C now days and GTK and Pango are - well - a "challenge".  

Anyone interested in my spagetti code is welcome to it as well.  Nothing to hide here!  ;)

---

### Post by anewguy on 2012-03-22
Just to let you know - I haven't had a chance to do this yet.  I had a little accident in the driveway trying to assembled a smoker and using a non-cooperative lawn chair.  With my bad back it was not pleasant.  Laid on top of a completely flattened lawn chair - back, legs and all - on a wet driveway in 60 degree weather last night for over 2 hours before someone went up the street that I could yell to help for.  The E.R. says I sort of hyper-aggravated the nerves in the bottom of my back that are bad to begin with.  Tough walking, and I was already scheduled for another epidural in my lumbar/sacral region for Friday as it is.  So, things aren't very pleasant right now and may not be for a while.

I'll let you know when I can finally get back to that.  Using a netbook like this while lying in bed isn't the easiest thing for me, and I sure don't want to try programming this way!

Thanks again for your input!

Dave ;)

---

