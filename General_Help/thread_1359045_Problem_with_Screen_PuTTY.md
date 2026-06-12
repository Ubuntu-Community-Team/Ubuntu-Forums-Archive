---
title: "Problem with Screen PuTTY"
date: 2009-12-19
forum: General Help
---

### Post by ND_con1986 on 2009-12-19
Hi, I am having a problem with the PuTTY instruction screen. I am running MATLAB with remote access on the computers of my school. Since a simulation might take up to 2 days and i do not want to keep my connection on PuTTY open, people suggested me using screen so that the session is running detached even if I am disconnected. The problem i am having is this: My code at some point saves the results in a .mat file in a sub-folder of the root directory of my platform. If I am logged in PuTTY snd detach the screen there is no problem with the running MATLAB session.

If I detach the screen and then logout then when I log back in to collect the results i get the following message  
"Error using ==> cd
Cannot CD to Directory (Name is nonexistent or not a directory)."

I changed my code to save results on the root directory of my platform to avoid this. Then when I log out and come back later I get the following message
"Error using ==> save
Unable to write file Filename.mat: permission denied."

Note that I have full rights on the space i have been given (rwx). As I said if I am logged in then there is no problem with the detached screen, running the session. But if I log out it is as if the running session has limiting rights. 

Any suggestions??? Thanks :-)

---

