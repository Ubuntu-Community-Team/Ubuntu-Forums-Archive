---
title: "how can i view terminal a-z"
date: 2010-06-09
forum: General Help
---

### Post by OxentroT on 2010-06-09
Sorry if this is silly but would like to know how I can set Terminal to display results a-z. For example when I put through the command 'dpkg --list' it will only show me listing from l-z.

thankyou all for any help:guitar:

---

### Post by quadproc on 2010-06-09
> **OxentroT said:**
> Sorry if this is silly but would like to know how I can set Terminal to display results a-z. For example when I put through the command 'dpkg --list' it will only show me listing from l-z.

I am not sure what is happening in your situation but I think that you may simply be seeing the first half of your output scroll off of the top of the screen.  If this is the case then you can use the vertical scroll bar (which is located at the side of the terminal window) to see what went past; put the cursor onto the bar at the top where the ^ symbol is, click the left mouse button once for each line that you want to raise the text.

Another way to see parts of output which is too large for the window is to make the window bigger.  Put the cursor onto the top edge of the window, push the left mouse button, and drag the top up as much as you like.

Another method is to use the _more_ utility: type
```
dpkg --list | more
```and the output will fill the screen and then wait for you to hit a space.  If you have seen enough then you can type q and it will quit.  Try reading the manual entry for more to learn more:
```
man more
```Or, I may have completely missed the nature of your problem.  If so then please ask again with more detail.

Good luck!

quadproc

---

### Post by nemilar on 2010-06-09
You should use less instead of more.  I'm not sure if Ubuntu just symlinks more to less, but it's good to get in the habit of using less -- it is more powerful.  Less is more :)

---

### Post by quadproc on 2010-06-09
> **nemilar said:**
> You should use less instead of more.  I'm not sure if Ubuntu just symlinks more to less, but it's good to get in the habit of using less -- it is more powerful.  Less is more :)
The two programs _more_ and _less_ are different code files in 9.10 so one is not a link to the other, but yes, _less_ is better.  I suggested more because it is simpler to learn but an experienced user will be better served by _less_.  Thanks for the recommendation.

quadproc

---

### Post by Zemblan on 2010-06-09
Far from being an expert in this sort of thing. But, if you want to filter out results from dpkg so that it only displays certain portions of the alphabet, say A to M, or C - K or whatever, I believe this will work

```
dpkg --list | grep ^..\ \ [m-z]
```

Just change the letters in [m-z] to whatever segment of the alphabet you are interested in. This particular regular expression will only work for 'dpkg --list' but you probably get the idea. The tools you need are 'grep' and possibly 'awk' or 'sed'.

EDIT: I think I have misunderstood your problem here, and the above answers about using 'less' are more appropriate. The only reason you don't see the full listing is that your terminal scroll buffer is too small to contain all the lines of output. 'Less' allows you to capture all that output and move around in it.

---

### Post by OxentroT on 2010-06-10
SUPERB. I find all of your advices to be of much help. 

Thank you all and rock on!:guitar:

---

