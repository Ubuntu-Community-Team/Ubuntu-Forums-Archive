---
title: "Getting HP Printer to print in reverse order (Lucid 10.04)"
date: 2010-06-17
forum: General Help
---

### Post by HyperFlexed on 2010-06-17
I solved this one today, so I figured I'd put up the solution for anyone else that needs it. If you've already tried using HPLIP without any effect, fear not, through a little text file hackery you can be on your way.

```
sudo nano /etc/cups/ppd/PrinterName.ppd
#Press tab to see your options if you're not sure what PrinterName.ppd should be
```

Add the following line to the file at the end (I leave some space so I know this is my own change to the file)

```
*DefaultOutputOrder: "reverse"
```

Now save the file and give it a test. I just made a document with "Page 1" on the first page, and "Page 2" on the second. It finally came out in the right order. :)

I imagine HPLIP should handle this for me, but it doesn't. Its usefulness has been relegated to checking ink levels.

---

