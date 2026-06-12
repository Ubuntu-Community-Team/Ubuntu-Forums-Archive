---
title: "Windows are automatically closing when I open them"
date: 2009-11-02
forum: General Help
---

### Post by Shaolin3666 on 2009-11-02
Hello,

I have been using and customizing Ubuntu for a while now. After going in and applying a lot of the recommended installs from the a/v threads I have created an issue I am having problems solving. If I open a window (this is noticed when I try to navigate to "computer" "network" or :camera" if connected. The task bar will say it's opening the item and then it closes immediately. I can open programs and they experience no issue. Any help would be greatly appreciated. Thank you

I am on release 9.04

---

### Post by Shaolin3666 on 2009-11-03
The list of items I performed is in this post [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I only did ones specific to my distro and what I needed.

---

### Post by dchurch24 on 2009-11-03
Have you tried opening the applications from the terminal?

If so, do you get any errors there?

---

### Post by Shaolin3666 on 2009-11-03
I will try that asap. What's the command to open say the computer window.

---

### Post by dchurch24 on 2009-11-03
I'm not sure what you mean by computer window.

However, if you mean the file browser (like Windows Explorer), then open the terminal and type:

```

nautilus

```

...and then check the terminal to see if there are any errors.

---

### Post by Shaolin3666 on 2009-11-04
The computer window I am talking about is the computer shortcut located in the "places" menu. I typed nautilus in the terminal window and the browser there came up just fine without error.

---

### Post by dchurch24 on 2009-11-04
I believe that would be nautilus.

What happens if you click 'Computer' then 'camera' (or whatever) in nautilus? Do you get an error in the Terminal window then?

---

### Post by Shaolin3666 on 2009-11-05
There isn't a computer link in the browser when I open it via nautilus.But I can open anything in that list no problems. Opening the computer link within the menu doesn't create an error in terminal either.

---

### Post by Shaolin3666 on 2009-11-09
Success,

Not quite sure it's a solution or not. But I upgraded to Karmic and it got rid of this issue. I am thinking I had a half installed/upgraded Karmic sitting there and that's what was causing it. But nonetheless, it's been resolved now.

---

