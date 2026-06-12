---
title: "Wget: how to get saved filename in bash script?"
date: 2010-04-04
forum: General Help
---

### Post by robbertnl on 2010-04-04
I want to make à bash script for downloading files. I want to write à file with the original URL and the filename wget gots from the server. I don"t want to force the filename.
I think that i have two solutions:
-parsing the wget output, but that is à little hard for me because of THE special chars in the output

-parsing the output of ls -t |head -2|tail -1 but that doesnt work since wget uses the remote time instead of the current time



So i am not sure what to do and maybe there are better solutions.

i want to do this for à lot of files, so manually is not an option

---

