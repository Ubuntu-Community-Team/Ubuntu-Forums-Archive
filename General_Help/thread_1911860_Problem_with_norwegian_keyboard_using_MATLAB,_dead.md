---
title: "Problem with norwegian keyboard using MATLAB, dead keys."
date: 2012-01-19
forum: General Help
---

### Post by Norwegiandude on 2012-01-19
So I installed MATLAB for school and I can't get the " ^ " key to work, which is quite important (3^2=9 etc). I have searched around on the internet and I think that the problem comes from the use of utf-8 instead of UTF-8 in the keyboard settings. I've tried these websites without luck:

[http://www.mathworks.com/matlabcentral/newsreader/view_thread/248237](http://www.mathworks.com/matlabcentral/newsreader/view_thread/248237)
[http://www.anders.bennehag.com/blog/2010/matlab-and-ubuntu-10-04/](http://www.anders.bennehag.com/blog/2010/matlab-and-ubuntu-10-04/)

I also get the same message when i start MATLAB:
"Warning: X does not support locale nb_NO.utf8"

I've tried both of these solutions, but either i don't have to folders needed to do the terminal scripts, or i don't know where to look. Would be much grateful for your help :)

---

### Post by Norwegiandude on 2012-02-05
I fixed it! I didn't need to change any settings using the terminal. I just switched "Norge" with "Norge Eliminate dead keys" in the keyboard settings, using the "Norge Eliminate dead keys" as the preferred option, and the circumflex worked instantly.

---

