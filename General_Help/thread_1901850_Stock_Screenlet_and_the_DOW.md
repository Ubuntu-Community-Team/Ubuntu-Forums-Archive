---
title: "Stock Screenlet and the DOW"
date: 2011-12-29
forum: General Help
---

### Post by defaria on 2011-12-29
For a while now my Stock Screenlet for the DOW has been broken. I would use ^dji as the symbol as that's the symbol used at http://finance.yahoo.com/q?s=^dji. But when I use that get "Wrong Symbol".

I changed the symbol to indu and for a while that seemed to work but then it broke again. Now starting up the stocks screenlet crashes unless I remove the indu stock.

I looked into the code a bit and AFAICT it does essentially the following to get a stock quote:


```
#!/bin/bash
wget -qO - "http://download.finance.yahoo.com/d/quotes.csv?f=nl1c1&s=$1"
```

Using this simple stockquote script I see:

```

Earth:stockquote goog 
"Google Inc.",638.96,-0.74
Earth:stockquote ^ixic
"NASDAQ Composite",2607.85,+17.87
Earth:stockquote ^gspc
"S&P 500",1259.72,+10.08
Earth:stockquote ^dji
Missing Symbols List.

```

So it seems the problem is that finance.yahoo.com returns bad data. I would have thought that at least some people are using the Stocks screenlet and that at least some people are trying to keep tabs on the DOW. Why has this not been reported before? 

And how do I fix this?

---

### Post by Guido Tabbernuk on 2011-12-30
For me it works using the latest Screenlets from Dev PPA. What version are you using? Stocks screenlet was updated in August 2011 ([http://bazaar.launchpad.net/~indiv-screenlets-dev/indiv-screenlets/trunk/revision/1038](http://bazaar.launchpad.net/~indiv-screenlets-dev/indiv-screenlets/trunk/revision/1038)) and new version was added to Screenlets in October 2011 ([http://bazaar.launchpad.net/~indiv-screenlets-dev/indiv-screenlets/trunk/revision/1068](http://bazaar.launchpad.net/~indiv-screenlets-dev/indiv-screenlets/trunk/revision/1068)).

---

### Post by defaria on 2012-01-12
Mine says Stocks 0.4 by Patrick Kullman. You don't say what symbol you are using. Can you show me the output of executing my little script on the symbols I list as well as identify which symbol you are successfully using?

---

### Post by Guido Tabbernuk on 2012-01-13
Try the one from Indiv-Screenlets. It has lower version number (0.2.4+) but was updated lately. I'm using ^DJI in my Stocks screenlet and it works.

---

### Post by defaria on 2012-01-13
What is "Indiv-Screenlets"?

You didn't tell me what you got for output using my little script (really just wget) and your symbol (^dji).

---

### Post by defaria on 2012-01-23
Can somebody who has this screenlet working for ^dji do a:

```
wget -qO - "http://download.finance.yahoo.com/d/quotes.csv?f=nl1c1&s=^dji"
```

And post the results?

---

### Post by defaria on 2012-01-28
Anybody else?

---

### Post by defaria on 2012-06-14
Is there a particular reason why nobody can see to copy that single line into a bash shell and post the results back to me?

---

### Post by wojox on 2012-06-14
Missing Symbols List. - is what i get.

---

### Post by wojox on 2012-06-14
```
wojox@wojox-laptop:~$ wget -qO - "http://download.finance.yahoo.com/d/quotes.csv?f=nl1c1&s=^DJIA"
"^DJIA",0.00,N/A

```

---

### Post by defaria on 2012-07-18
So then you both verified what I've already experienced. This is broke, broke, broke. When ^dji is given you get missing symbol list. This is wrong as the ^dji works on Yahoo's web site.

If you use ^djia then you get back 0.00. You don't really think that the Dow dropped 12000 points and hit exactly 0.00 do you? IOW if you used "XXXX" for the symbol you get the exact same thing.

I'm shocked that this, probably the most watched index in the world, is broken and nobody 'cept little ole me seems to have noticed it...

Now does anybody know how this can be fixed?

---

