---
title: "PHP / Javascript Question"
date: 2010-11-13
forum: General Help
---

### Post by cearlp on 2010-11-13
Since updating to 10.10 on a new machine and moving my PHP code from 9.04 to the 10.10 environment I seem to be missing the software I need for the php program to execute some javascript. 

This code in the program works:
        <script type="text/javascript">
           function redirect() {
              window.location="<?php echo $_SERVER['PHP_SELF']; ?>";
           }
        </script>

This does not:
  function confirm($msg) {
    echo "<script langauge=\"javascript\">alert(\"".$msg." </script>";
  }

Any suggestions will be greatly appreciated.

---

### Post by cearlp on 2010-11-13
This seems to be a Firefox problem. After the alert box is displayed the page is still loading. Hitting the escape key allows me to try the resubmission again and sometimes I get the entire alert box with the correct message dispalyed.
It works correctly using Safari or IE4 as the browser.

---

### Post by SeijiSensei on 2010-11-13
I know a lot more about PHP than Javascript, but in general, Javascript doesn't use dollar signs to denote variables.  See [this](http://en.wikipedia.org/wiki/JavaScript_syntax).  (Dollar signs are allowed but are not common in most scripts I've examined.)  They're also usually declared with a "var" statement.  I've also not seen variables that use dollar signs defined as function arguments.

It looks to me like your second example is rather a mix of PHP and Javascript syntax.

---

### Post by cearlp on 2010-11-14
The code examples are from a file written in PHP syntax.
The code is valid and works using any browser as long as the browser is not the latest Ubuntu Firefox.

---

### Post by WorMzy on 2010-11-14
> **cearlp said:**
> This does not:
function confirm($msg) {
echo "<script langauge=\"javascript\">alert(\"".$msg." </script>";
}

Does the msg variable end with
```
")
```
?

If not, then what you have there is an unclosed function. Once PHP has finished processing it, it'll read as such:
```
<script langauge="javascript">alert("message </script>
```

You also spelt "language" wrong, and anyway, it should be ```
type="text/javascript"
```
like your first bit of code.

---

### Post by cearlp on 2010-11-14
Thanks for the spelling lesson WorMzy. Dyslexic fingers!

The odd thing is that the code works if I use any browser except the Firefox in Ubuntu. Firefox on the Mac, IE on Windows 7 and Chrome on either work just fine.

The msg variable in the PHP file looks like this:
$msg = "Record successfully added";

the call looks like this:
confirm($msg);

and the function looks like this:
function confirm($msg)
{
  echo "<script language=\"javascript\">alert(\"".$msg."\");</script>";
}

Disabling Firefox plugins didn't change the result so I enabled them all again and the code worked. But when I restarted Firefox
it failed again. I can't seem to isolate the exact conditions that cause the failure or success of the execution of the code.

---

### Post by WorMzy on 2010-11-14
I couldn't say for sure why that is, but it may have something to do with your browser's cache. Try clearing it (Ctrl+Shift+Delete) and seeing if that helps. Your code is still not valid though. If it works at all, it's just because the browsers are feeling generous; the script tag has no "language" attribute, so you haven't actually told the browser that your script is Javascript.

Also, I hope you realise that PHP cannot execute Javascript. PHP is a server-side script, whereas Javascript is a client-side script. It just seems odd to me that you have a PHP function for the sole purpose of writing of a javascript function, but I'm sure you know your own code best.

---

### Post by cearlp on 2010-11-15
Again, thanks WorMzy.

I changed the syntax of the script tag to follow html rules. It works the same as my erroneous syntax.

The PHP file is generating html code for the browser and the script is simply to get an alert box containing the 'msg' to popup on the displayed page.
If I don't use a script the 'msg' simply prints out on the page that is already on the screen.

Clearing the cache causes things to work correctly for two or three times but on the subsequent transmission the alert box pops up, but with no msg displayed, and the browser hangs indicating that the page is in the process of being loaded but not completed. Clearing the cache again causes  the same scenario -- works a few times then fails.

The version of Firefox that Ubuntu has simply does not function the same as other versions of FIrefox.

---

### Post by WorMzy on 2010-11-15
I guess it could be the browser at fault, though I've never had this problem myself. Does the page work fine in Chromium, Opera, Midori, etc, on Ubuntu?

---

### Post by cearlp on 2010-11-15
I haven't installed any other browser on my Ubuntu machine. But I have Chromium. Firefox and Safari on my Mac. It works fine on all of them. 
I'll try to get some other browsers on my Ubuntu installation and see what happens.

---

