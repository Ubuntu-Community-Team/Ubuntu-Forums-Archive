---
title: "problem on Auction Arms website"
date: 2011-04-16
forum: General Help
---

### Post by wpshooter on 2011-04-16
Can I get someone that is using Ubuntu/Lucid and Firefox as browser to run a test for me ?

Can you go to this website and then type the either the word "HIGH" or the word "LOW" in the search box and then tell me if you get the same bunch of program error codings that I get when I try this ?

Wanting to see if this is a problem with just my computer setup or with the websites programming.

[http://shop.auctionarms.com/guns/nra-used-grades](http://shop.auctionarms.com/guns/nra-used-grades)

Thanks.

---

### Post by plucky on 2011-04-16
```
Server Error in '/' Application.
Argument 'Length' must be greater or equal to zero.
Description: An unhandled exception occurred during the execution of the current web request. Please review the stack trace for more information about the error and where it originated in the code.

Exception Details: System.ArgumentException: Argument 'Length' must be greater or equal to zero.

Source Error:

Line 1709:            '--------------------------------------------------------------BEGIN PRICE
Line 1710:            If Left(e, 3) = "low" Then
Line 1711:                If IsNumeric(Right(e, e.Length - 4)) Then
Line 1712:                    _QS(9) = e
Line 1713:                    AH.Value = e.Remove(0, 4)


Source File: C:\AUCTIONARMS\shop\auctions.aspx.vb    Line: 1711

Stack Trace:

[ArgumentException: Argument 'Length' must be greater or equal to zero.]
   Microsoft.VisualBasic.Strings.Right(String str, Int32 Length) +746133
   search.auctions.Word_Check(String e) in C:\AUCTIONARMS\shop\auctions.aspx.vb:1711
   search.auctions.Parse() in C:\AUCTIONARMS\shop\auctions.aspx.vb:1611
   search.auctions.SEO_Check() in C:\AUCTIONARMS\shop\auctions.aspx.vb:1517
   search.auctions.Page_Load(Object sender, EventArgs e) in C:\AUCTIONARMS\shop\auctions.aspx.vb:375
   System.Web.UI.Control.OnLoad(EventArgs e) +132
   System.Web.UI.Control.LoadRecursive() +66
   System.Web.UI.Page.ProcessRequestMain(Boolean includeStagesBeforeAsyncPoint, Boolean includeStagesAfterAsyncPoint) +2428

```

This is what I get on Lucid with Firefox.

Hope this helps

---

### Post by wpshooter on 2011-04-16
> **plucky said:**
> ```
Server Error in '/' Application.
Argument 'Length' must be greater or equal to zero.
Description: An unhandled exception occurred during the execution of the current web request. Please review the stack trace for more information about the error and where it originated in the code.

Exception Details: System.ArgumentException: Argument 'Length' must be greater or equal to zero.

Source Error:

Line 1709:            '--------------------------------------------------------------BEGIN PRICE
Line 1710:            If Left(e, 3) = "low" Then
Line 1711:                If IsNumeric(Right(e, e.Length - 4)) Then
Line 1712:                    _QS(9) = e
Line 1713:                    AH.Value = e.Remove(0, 4)


Source File: C:\AUCTIONARMS\shop\auctions.aspx.vb    Line: 1711

Stack Trace:

[ArgumentException: Argument 'Length' must be greater or equal to zero.]
   Microsoft.VisualBasic.Strings.Right(String str, Int32 Length) +746133
   search.auctions.Word_Check(String e) in C:\AUCTIONARMS\shop\auctions.aspx.vb:1711
   search.auctions.Parse() in C:\AUCTIONARMS\shop\auctions.aspx.vb:1611
   search.auctions.SEO_Check() in C:\AUCTIONARMS\shop\auctions.aspx.vb:1517
   search.auctions.Page_Load(Object sender, EventArgs e) in C:\AUCTIONARMS\shop\auctions.aspx.vb:375
   System.Web.UI.Control.OnLoad(EventArgs e) +132
   System.Web.UI.Control.LoadRecursive() +66
   System.Web.UI.Page.ProcessRequestMain(Boolean includeStagesBeforeAsyncPoint, Boolean includeStagesAfterAsyncPoint) +2428

```

This is what I get on Lucid with Firefox.

Hope this helps

Have any ideas as to what is causing this ?

I e-mailed this to the website owner and they said that they could not replicate this problem, but I suspect they were probably trying it on a M/S windows IE computer.

In any case they have seemly made no efforts to fix this.

Thanks.

IT HAS BEEN FIXED NOW.  THANKS.

---

