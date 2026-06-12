---
title: "awk in bash.bashrc"
date: 2009-06-30
forum: General Help
---

### Post by motoperpetuo on 2009-06-30
i have a dell latitude d610 laptop, running ubuntu 9.04. if i enter the follwing command in the shell, i get the CPU temperature, expressed as an integer with no additional output:
```

cat /proc/acpi/thermal_zone/THM/temperature | awk '{print $2}'

```
what i would like to do is add this as an alias to bash.bashrc. so far i've come up with this:
```

alias fantemp="cat /proc/acpi/thermal_zone/THM/temperature | awk '{print $2}'"

```
this sort of works, but it just prints out the full contents of /proc/acpi/thermal_zone/THM/temperature, for example, something like this:

temperature:             52 C

whereas i'd really rather just have the integer value as output.

i've tried other combinations of quotes, double-quotes, and back ticks around the alias in bash.bashrc, but most of them do the same or give me an error about a missing } at the end of the line.

does anyone know if it would be possible to get this awk statement to work in bash.bashrc as it does in an interactive shell?

---

### Post by t4thfavor on 2009-06-30
it appears to be the print $2 is  not working because the double single quotes. Theres gotta be a way, we just are missing it.

got it;

```

function temp()
{
        cat /proc/acpi/thermal_zone/TZ00/temperature |awk '{print $2}';

}

```

then just run temp.

---

### Post by motoperpetuo on 2009-06-30
excellent, that worked perfectly. thank you very much.

i had to change your TZ00 directory back to THM, of course, which is what i have on my computer. i've played around with fan and temperature settings a bit and noticed that they're different in different distros and on different computers. out of curiosity, does anyone know what determines that?

---

### Post by t4thfavor on 2009-07-01
chipset, and type of sensors used to make your pc. It's all about which driver the kernel uses for your gear.

Sorry, I had to change your THM to TZ00.

---

### Post by Brandon Williams on 2009-07-01
The alias method needed to escape the '$' in '$2' so that it would not be interpreted by the shell. The quoted single-quotes don't have the effect of escaping '$2'. The command should have been:
```
alias fantemp="cat /proc/acpi/thermal_zone/THM/temperature | awk '{print \$2}'"
```

---

### Post by t4thfavor on 2009-07-01
Ahh I tried escaping all kinds of stuff, I never thought that would have been it. Well either way works, I kinda like that I learned about functions in .bashrc. Thanks a bunch.

---

### Post by motoperpetuo on 2009-07-02
thanks again to both of you for your answers to both of my questions.

---

