---
title: "Firefox keeps autoselecting input fields while I type...?"
date: 2011-02-14
forum: General Help
---

### Post by k999 on 2011-02-14
Hi,

I'm having a weird issue with Firefox on several computers, though on some it's more prevalent than others.

When I start Firefox, I can type in text in the address field or google search field, and all works as normal. Suggestions pop up, and when I'm done I can select my text or a suggestion and go for it.

However, after a few minutes of browsing, something strange (almost?) always happens. As I type in text (most commonly in the google search field), the text is auto-selected while I'm typing. When that happens, the next character I press deletes the entire text I've written so far, and starts over. So I keep deleting the text I'm typing, all the time, and it's extremely annoying and kills my productivity.

If I type fast enough it doesn't happen, but I type pretty fast (people tend to think I know touch, but I don't), and just a small pause while hitting a more difficult to reach key triggers this, so it happens all the time. Sometimes it's only the google search field that is affected, sometimes it's the address field as well, and in the worst case it's the google page text input as well, though this usually doesn't happen. Other pages don't seem to be affected much.

I'm stumped on this one. It's a laptop, and I've stopped using the built in keyboard/mouse (both are now external USB devices), but it still happens. I've seen similar issues on a Toshiba, a Fujitsu and a Dell laptop, so I don't think it has anything to do with hardware. And I've only experienced it in Firefox on Ubuntu 10.10 (and maybe 10.04, don't remember for sure). I have Firefox on Windows as well, and never experienced it there.

Could it be a weird bug that has something to do with javascript? I use google apps for email, and on one computer, when I type in "mail" in the address bar, the address should have appeared because it's bookmarked, but it doesn't... and after that failure, I usually notice that the weird autoselect-bug has been triggered. But I think there must be other triggers as well, because it does appear even though I stay away from my email.

Any tips would be much appreciated!

---

### Post by Habitual on 2011-02-14
Turn off/'Do not use' "Google Instant" at google.com

---

### Post by k999 on 2011-02-16
But I want that feature, and it works on Firefox on Windows (and Ubuntu 9). And what does that have to do with my address field? Is this a bug in Firefox? Aren't other people affected by this?

---

### Post by dirkvs on 2011-02-16
I get this too. It doesn't always happen, but when it starts, it won't stop until I restart the browser.

And it's not just the search box - it's any input field. Search box, address bar, and all text input boxes within web pages.

When this happens, I work around it by typing the text in gedit, and then copy/paste into Firefox.

Edit: Using Ubuntu 10.10 and Firefox 3.6.13

---

### Post by fyo on 2011-02-16
> **k999 said:**
> But I want that feature, and it works on Firefox on Windows (and Ubuntu 9). And what does that have to do with my address field? Is this a bug in Firefox? Aren't other people affected by this?

I am. Two different systems (differing in version of Ubuntu & Firefox), both affected, although for some reason, it happens A LOT on my netbook. It never happens for me on my desktop, but it happens for my wife (separate account) all the time.

Symptoms are exactly as you describe.

Incredibly annoying.

Now... While I haven't found the root cause of this (and this was the only thread on it I found with a few searches... which seems really odd, 'cause I've been having the problem for months), I do have some "clues":

-> I've been able to get it to revert to normal on my laptop by randomly jabbing at a bunch of keys / touchpad. I haven't been able to isolate the combination (not a single key) that does it, but SOMETHING does work.

-> I can consistently get it to revert by opening the Ubuntu "Keyboard Shortcuts" application. I don't have to do anything in it, just open it and close it again (which may not even be necessary, but I haven't tried).

-> So apparently, the "state" can be switched off and there's both some keyboard/touchpad combo that does it as well as it being reset when "Keyboard Shortcuts" is opened.

-> I'm not experiencing this issue with any other applications. Just FF.

-> I'm *fairly* sure I haven't experienced the issue while continually using Firefox. It always (I think) happens after I've either used other programs (maybe) or (more likely) the screen saver / screen turn off has kicked in. Maybe even a suspend to memory.

---

### Post by fyo on 2011-02-16
> **Habitual said:**
> Turn off/'Do not use' "Google Instant" at google.com

This appears to have nothing to do with Google Instant. My searches go through Firefox's search bar and the issue occurs with Firefox's [s]address[/s] awesome bar and search bar.

---

### Post by k999 on 2011-02-16
Yes, that's what I get too. It seems to hit any input field (in browser or on web pages) that shows suggestions, and when this happens, it seems to just select the text I'm typing _instead_ of showing the suggestions. 

When this affects me, I can type something like "poiqwep" into the google search field, and that's fine, because google doesn't have any suggestions for that. But if I type "asdasdasdasdasd" I still get trouble, because google _does_ have suggestions for that. 

I've found the same workaround as dirkvs. But this copy/paste workaround gets very tedious after a while...

---

### Post by ubu_seth on 2011-03-13
Hi!

I've got the same problem for months in various text inputs, e.g., very often when I try to write an edit summary in wikipedia.

It seems to occur only in the combination of firefox and ubuntu systems. Is it a firefox or a ubutu problem? Does anybody know, how to fix it?

bye
seth

---

### Post by k999 on 2011-03-13
I started this thread a while ago, and I still have the same problem. I'm surprised there aren't more complaints, actually. It's incredibly irritating. I use Ubuntu for work, and keep getting my workflow interrupted by this. I've spent hours trying to diagnose and fix it, but I guess I haven't been systematic enough, because I haven't found anything.

I've had this problem on many computers, with both Ubuntu 10.04 and 10.10, and I have different sets of plugins installed. I've not experienced this on Windows, only Ubuntu, so it appears to be an Ubuntu/Firefox combination issue.

---

### Post by luotinen on 2011-03-28
Bug confirmed in Ubuntu 10.04 with Firefox 3.6.16.

---

### Post by k999 on 2011-04-05
OK, I think I'm on to this bug!!

When I search on google in Firefox, I almost always do this:

[LIST=1]
[*]Hit ctrl-t to open a new "tab"
[*]Hit the tab key once to move the cursor to the search field
[*]Start typing the search phrase
[/LIST]

But I've discovered now that if I **point and click with the mouse** in the search field to move the cursor there, instead of tabbing the cursor to get there with the keyboard, then this doesn't happen!

That could explain why so few people are complaining, I guess... It only hits people who are fanatic keyboard users. Can anyone else on this thread confirm this?

---

### Post by k999 on 2011-04-05
By the way, the reason I discovered was that I opened google in a new window, and then for whatever reason tabbed my way all through the browser buttons and top links to get to the search field, and then I got this same problem there. But by clicking in the search field, it wasn't a problem. 

While I have experienced this before on a web page, it doesn't happen anywhere near as often as it does in the browser search field, so this led me to think it was something about my usage causing this bug.

---

### Post by jcac on 2011-04-22
I was hoping to find a fix to my problem, but since this is all I can  find about it online I'll at least offer up my own 2 cents of symptoms, as I think it's the same thing.

I'm using Linux Mint (so it's probably not ubuntu-specific), and having the same trouble, EXCEPT that it hasn't *ever* seemed to be a problem for text boxes *within* a website: just the address bar and search bar built into firefox.

Typing speed doesn't seem to have any impact on it for me as initially suggested: I often go too fast for my buffer and when it does all spill out I can see each letter individually flash across my screen and get deleted in turn for the next letter. My computer's 6 years old though (might be old computer issue?).

I will try to notice if there's any correlation to mouse/keyboard opening of a new tab: I always use ctrl+t like everyone else here. I know using the mouse to switch between the address bar and search bar has been useless in the past, but it might be that using the mouse keeps the trouble from starting initially but won't fix it once it's already autoselecting.

Possible workaround without restarting the browser: Today it gave trouble and I found that if I loaded a page (home page, bookmark, whatever) on my new tab that I could then type in the navigational fields as normal, so it seemed to "reset" the bug. I don't know if it will work every time or I was just lucky: it hasn't acted up again for me to test it.

Hope it helps someone!

~

---

