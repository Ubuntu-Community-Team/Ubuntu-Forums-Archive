---
title: "emacs -fs eats the minibuffer"
date: 2010-11-11
forum: General Help
---

### Post by gunksta on 2010-11-11
I would like to use emacs -fs on my netbook (for obvious reasons). I am running a relatively default version of ubuntu-desktop on the netbook. I am not running the netbook edition.

emacs -fs and emcs -q -fs result in a full screen, but I can't see the minibuffer. I tried this with the two gnome-panels set to autohide and not not hide. Same result.  See attached screen shot. I am interested to know if others are having this problem and if anyone has a solution.

---

### Post by gunksta on 2010-11-12
I also tried 'emacs -fh' and I get effectively the same end-result. The minibuffer is below the bottom of the screen.  In have used my init.el to set the height in the past but I am now sharing my configuration among several computers (one is a netbook) and I would like a simple way to have emacs adjust its height to fit the current environment.

---

### Post by Jskud on 2010-12-30
I had a similar problem with a new install of emacs 23.1.1 on ubuntu 10.10 on a netbook, and was able to show the minibuffer by going out of and back into full screen mode -- that is, click on the maximize icon at the top (for me, square box at the upper left, third icon over) twice.

I also found that if I avoid the tool-bar, then I get the minibuffer when I start up emacs.  I avoid the tool bar with the following in my .emacs file:

> (tool-bar-mode 0)

I still found that I need to go out of full screen mode (and then I go back in) to use all the screen real estate -- removing the too-bar appears to leave a gap at the bottom of the frame -- it _looks_ like the minibuffer is too big, but it is just unused real estate.

Hope this helps.  /Jskud

---

### Post by Terminal Upper Case on 2011-01-07
I might be wrong, but it sounds like you two are both talking about two separate issues, one with full screen mode putting the echo area off screen, and one with a maximised window (not an internal Emacs window of course) making the echo area too large.
Somehow I'm facing both of these issues. Having to resize a window twice before you can start editing sucks.

---

### Post by gunksta on 2011-01-07
I finally gave up and stopped using -fs. I just maximize emacs after it opens. It's not a very 'emacs-like' solution, but it 'works' on all of my systems.

The terminology emacs uses is, in today's world, unfortunate. While emacs predates the 'Windows' environment by years, the emacs-lingo inevitably leads to confusion. I remember when I first started using emacs -- pull, yank, windows - ??? 

Throw up a screenshot of what you are dealing with, maybe someone will have an idea.

-- Are you also using emacs -fs? 
-- What do you have in your init.el?

---

### Post by Terminal Upper Case on 2011-01-07
Screenshots? Okay, here's a bunch.
Picture 1 is what it looks like if I go through the soul crushing trouble of hitting the maximize button manually every time I launch emacs. Not bad, but as you can see there is a bit of a gap at the bottom of the echo area. If it started up like this I would be happy enough to continue living until I figured out how to get rid of the gap.
Picture 2 is what it looks like with an "-fs" argument and no toolbar. Note the enormous gap below the echo area. Unacceptable.
Picture 3 is "-fs" with the toolbar. As you mentioned, echo area is right off the page, along with most of the mode line. Broken.
Picture 4 is starting out with an altered .emacs file to automatically maximize the window, and no toolbar. I found the code on the emacs wiki. As with picture 2, there is a huge gap.
Picture 5 is with same altered .emacs file but with the toolbar. Echo area is off screen.

Here's the contents of my .emacs file as pertaining to Pictures 4 and 5:
```
(tool-bar-mode -1)

(defun toggle-fullscreen ()
  (interactive)
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
                 '(2 "_NET_WM_STATE_MAXIMIZED_VERT" 0))
  (x-send-client-message nil 0 nil "_NET_WM_STATE" 32
                 '(2 "_NET_WM_STATE_MAXIMIZED_HORZ" 0))
)
(toggle-fullscreen)
```
(note: I do not understand the syntax)

As for emacs terminology, I almost consider it a feature. It might be the sleep dep. from staying up too many nights reading man and info pages lately, but when I read that the PageDown key is mapped to the "scroll-up" command I laughed for quite a while.
 
Any light shed on my problem(s) here is appreciated.

---

### Post by Terminal Upper Case on 2011-01-10
Problem solved with version 23.2.1, which is not in the Ubuntu repository, obtained from [ftp://ftp.gnu.org/pub/gnu/emacs/]("http://ftp.gnu.org/pub/gnu/emacs/") . Both maximized frame and -fs full screen mode work perfectly on desktop and netbook right from launch. Other stuff works better and looks nicer too, including automatic resizing of window to fit on screen by default. Also an argument of -mm starts in full screen mode without the need for a script. I attached a screenshot of how starting up emacs with -fs looks on my netbook now. Hope this is helpful to other people with similar problems.

---

### Post by gunksta on 2011-01-10
That is very interesting. I assumed I was doing something wrong. When emacs behaves strangely I often assume that I am doing something wrong (my inti.el is rather spaghetti like). Failing that, I assume emacs is doing what it should and that I am somehow failing to understand.  :-)

Good to know that we're not all crazy.

---

### Post by xurizaemon on 2011-02-10
> **Terminal Upper Case said:**
> if I go through the soul crushing trouble of hitting the maximize button manually every time I launch emacs

Can I just add that this was bugging the hell out of me, but since reading your post, I mentally think "oh yes, the soul-crushing trouble" when I click maximise twice each time I launch Emacs, and laugh quietly to myself, and what was once an annoying bug becomes a source of personal amusement.

Thanks for your great attitude - it has allowed me to rest in my laziness and not bother rebuilding Emacs from source as suggested in later posts.

---

