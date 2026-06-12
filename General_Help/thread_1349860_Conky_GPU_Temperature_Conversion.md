---
title: "Conky GPU Temperature Conversion"
date: 2009-12-08
forum: General Help
---

### Post by RabidJawaMan on 2009-12-08
I have sorted through more posts that I can recall, and for the life of me I cannot find out how to integrate the formula to change the GPU's temperature output from Celsius to Fahrenheit.Here is an excerpt from my .conkyrc file, showing the three temperature outputs that I have.

```
Core1: ${alignr}${exec echo "`sensors | grep 'Core 0' | cut -c15-16`*9/5+32"|bc}F
Core2: ${alignr}${exec echo "`sensors | grep 'Core 1' | cut -c15-16`*9/5+32"|bc}F
GPU: ${alignr}${execi 60 nvidia-settings -t -q GPUCoreTemp}C
```

The different syntax for the GPU is really throwing me off, Any help that can be given would be greatly appreciated.

---

### Post by m_duck on 2009-12-08
Firstly, I think your 2 "Core" cpu lines will only execute once, then leave that one temperature in the conky window until it is closed/opened again. "exec" runs a command only once and posts its output, whilst "execi #" executes a command at an interval of # seconds. So I would change the **${exec echo "`sen...** to **${execi 60 echo...** for example.

As for the GPU temperature, you could change it to the equivalent style to you cpu temps like this:
```
${execi 60 echo "`nvidia-settings -t -q GPUCoreTemp` *9/5+32" | bc}
```What that does is execute **nvidia-settings -t -q GPUCoreTemp** and echoes the answer, along with ***9/5+32** and then pipes that to *bc* which carries out the calculation on the string which is given to it from the echo command. Sorry, that's really unclear but hopefully you get my drift...

---

### Post by RabidJawaMan on 2009-12-08
> **m_duck said:**
> Firstly, I think your 2 "Core" cpu lines will only execute once, then leave that one temperature in the conky window until it is closed/opened again. "exec" runs a command only once and posts its output, whilst "execi #" executes a command at an interval of # seconds. So I would change the **${exec echo "`sen...** to **${execi 60 echo...** for example.

As for the GPU temperature, you could change it to the equivalent style to you cpu temps like this:
```
${execi 60 echo "`nvidia-settings -t -q GPUCoreTemp` *9/5+32" | bc}
```What that does is execute **nvidia-settings -t -q GPUCoreTemp** and echoes the answer, along with ***9/5+32** and then pipes that to *bc* which carries out the calculation on the string which is given to it from the echo command. Sorry, that's really unclear but hopefully you get my drift...

I was starting to go crazy, thanks for the info I understand perfectly!

---

