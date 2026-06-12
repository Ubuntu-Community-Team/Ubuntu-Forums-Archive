---
title: "How can I force Evolution to open all links in background?"
date: 2010-07-19
forum: General Help
---

### Post by x-shaney-x on 2010-07-19
When checking emails, many will be notifications from forum threads or other internet links.
I have noticed it is very inconsistent in the way it opens them.
Sometimes the browser will stay in the background so I can keep reading the emails and keep clicking on the links for reading in the browser afterwards.
Other times the browser will jump to the front with every link so I have to keep switching back to Evo.

And other times it's a mix of both, seems completely random.

---

### Post by JustinR on 2010-07-19
What internet browser are you using?

---

### Post by x-shaney-x on 2010-07-19
mostly switching between chrome and firefox, happens with both.

---

### Post by JustinR on 2010-07-19
It could be a web browser issue. I use Opera and all of the URLs I click on in Evolution open in the background.

See if your browsers have anything about opening links in backgrounds.

If not,

go to System > Preferences > Preffered Applications. Under Web Browser make sure your default is selected then click 'Open link in new tab'.

---

### Post by x-shaney-x on 2010-07-19
After some more checking I noticed it is random when using firefox but chrome ALWAYS jumps to the front.

Setting firefox to open in new tab in that preference solves it with firefox and now it stays in the background all the time.

Chrome is still jumping to the front regardless.

<EDIT>
Nope, after setting the default back to firefox again with open links in new tab, it's jumping to the front again.

<EDIT> #2
Changing this about:config setting in firefox "browser.tabs.loadDivertedInBackground;false" to true finally seems to have sorted it with firefox.

Trouble is, I tend to use chrome more lately.

---

### Post by JustinR on 2010-07-19
Okay well try this (This is how I got opera to work)


Whichever default browser you want (Firefox or Chrome)
```

firefox/chrome --help

```

It should list commands, in this case the command to keep Opera in the background was -noraise.

So mine entry in Preferred Applications looks like this when I set the default internet browser to Custom:
```

opera -noraise %s

```

---

