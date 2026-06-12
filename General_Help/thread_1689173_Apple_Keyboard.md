---
title: "Apple Keyboard"
date: 2011-02-16
forum: General Help
---

### Post by BarataPT on 2011-02-16
Hi,

Recently i installed Ubuntu 10.10 on my laptop. I'm trying to use an Apple Aluminium Keyboard ([_Portuguese Layout_]("http://storeimages.apple.com/1501/as-images.apple.com/is/image/AppleInc/MB110PO?wid=1200&hei=1200&fmt=jpeg&qlt=95&op_sharpen=0&resMode=bicub&op_usm=0.5,0.5,0,0&iccEmbed=0&layer=comp")) but some of the keys are swapped.

I tried to change the keyboard's layout and tried all of them but some keys are always swapped. Keys like "^", "<", ">" or "|" are in wrong positions. Is there some way i can manually change this settings?

---

### Post by coffeecat on 2011-02-16
How did you try to change the layout? This works for me for an Apple keyboard in the UK which has quite a few keys in different positions from a standard PC keyboard.

Go to System > Preferences > Keyboard. Now the Layouts tab. Make sure you have Portugal as the default in the top pane. If not, add it. Now click on the Keyboard model. Choose 'Apple' under vendor and 'Apple Aluminium Keyboard' under model. I have three choices: ANSI, ISO and JIS and I don't know what the difference is. You could try each and test it in the 'Type to test settings' field.

Here's an Ubuntu community documentation page which might be of help:

[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

One problem I have never been able to get round is the lack of a SysReq key on an Apple keyboard for the magic key shutdown sequence.

---

### Post by BarataPT on 2011-02-17
Hi,

That was exactly what i did. I changed between the Aluminium modes but the problem remains.

When press the "Show Layout" for some reason the top left key (left of "1" key) is not recognized. And when i press the key with "< >" (right to the right-shift) it is mapped to be that key. 

The problems seem to be on the keys on the left and right corners. Here are some incorrect mappings ( key -> actual mapping without and with shift):
+/- (left of "1") -> "<" and ">"
"<" ">" (right of right_shift) -> "\" and "|" 
"*" "+" (left of backspace) -> "«" and "»"
"ª" "º" (right of "P") -> "+" and "*"

---

### Post by coffeecat on 2011-02-17
I've just discovered that in the Keyboard preferences window (Layouts tab), I have to add 'United Kingdom Macintosh' in the upper pane and make that the default for my aluminium keyboard to work. Just setting 'Apple Aluminium Keyboard' under Keyboard model doesn't work unless I do that. You can do the same with Portugal.

Even so, the key to the left of the numeric 1 doesn't work properly for me either. The key is inscribed with the § and ± characters, but I get < and > respectively, as you do.

The other keys you mention work OK for me, but from your description, I think there must be differences in the UK and Portuguese layouts. If you want to compare, here is the UK layout on the Apple website:

[http://store.apple.com/uk/product/MB110B/A](http://store.apple.com/uk/product/MB110B/A)

Apart from that, I'm sorry, I don't know what else to suggest.

---

### Post by BarataPT on 2011-02-18
I've changed the keyboard layout to "Macbook/MacBook Pro" and this way only two keys are swapped "§ and ±" key and "<>" key.

I only have one major problem now. Some key-combinations don't work. For example Alt+F2 or Alt+F4. If i press Alt+F2 it works like i'm trying to change the brightness. Don't know if i have to change some option to make this combinations work as usual. I tried left and right Shift, and Command but the result is always the same...

---

### Post by coffeecat on 2011-02-18
> **BarataPT said:**
> I only have one major problem now. Some key-combinations don't work. For example Alt+F2 or Alt+F4. If i press Alt+F2 it works like i'm trying to change the brightness.

I can't check this at the moment as I'm using a Logitech ketboard, but I think you have to press the Fn key as well as Alt+F2 to get the Alt+F2 shortcut. Without the Fn key, you get what you should get with the Fn key - if that makes sense. Confusing! It's partly described in the link I posted in post #2.

---

