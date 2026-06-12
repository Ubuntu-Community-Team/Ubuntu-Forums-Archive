---
title: "bash: anyone know a better way to do this?"
date: 2010-09-05
forum: General Help
---

### Post by d3v1150m471c on 2010-09-05
i'm building a dictionary with a bash script. it works perfect except i'd prefer something faster. btw i'm just piping the output to a file.

```

#!/bin/bash

export NUM="0"
export A="0"
export B="0"
export C="0"
export D="0"
export E="0"
export F="0"
export G="0"
export H="0"
export I="0"
export J="0"
export K="0"
export L="0"
export M="0"
export N="0"
export O="0"
export P="0"
export Q="0"
export R="0"
export S="0"
export T="0"


SCROLL() {
          head -$NUM ~/characters | tail -1
                                          }

FIXED_A() {
          head -$A ~/characters | tail -1
                                        }

FIXED_B() {
          head -$B ~/characters | tail -1
                                        }

FIXED_C() {
          head -$C ~/characters | tail -1
                                        }

FIXED_D() {
          head -$D ~/characters | tail -1
                                        }

FIXED_E() {
          head -$E ~/characters | tail -1
                                        }

FIXED_F() {
          head -$F ~/characters | tail -1
                                        }

FIXED_G() {
          head -$G ~/characters | tail -1
                                        }

FIXED_H() {
          head -$H ~/characters | tail -1
                                        }

FIXED_I() {
          head -$I ~/characters | tail -1
                                        }

FIXED_J() {
          head -$J ~/characters | tail -1
                                        }

FIXED_K() {
          head -$K ~/characters | tail -1
                                        }

FIXED_L() {
          head -$L ~/characters | tail -1
                                        }

FIXED_M() {
          head -$M ~/characters | tail -1
                                        }

FIXED_N() {
          head -$N ~/characters | tail -1
                                        }

FIXED_O() {
          head -$O ~/characters | tail -1
                                        }

FIXED_P() {
          head -$P ~/characters | tail -1
                                        }

FIXED_Q() {
          head -$Q ~/characters | tail -1
                                        }

FIXED_R() {
          head -$R ~/characters | tail -1
                                        }

FIXED_S() {
          head -$S ~/characters | tail -1
                                        }


###########################################################
# test bytes

PRINT() {
while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="0" && A=`expr $A + 1`

[ $A -eq 94 ] && A="1" && B=`expr $B + 1`
[ $B -eq 94 ] && B="1" && C=`expr $C + 1`
[ $C -eq 94 ] && C="1" && D=`expr $D + 1`
[ $D -eq 94 ] && D="1" && E=`expr $E + 1`
[ $E -eq 94 ] && E="1" && F=`expr $F + 1`
[ $F -eq 94 ] && F="1" && G=`expr $G + 1`
[ $G -eq 94 ] && G="1" && H=`expr $H + 1`
[ $H -eq 94 ] && H="1" && I=`expr $I + 1`
[ $I -eq 94 ] && I="1" && J=`expr $J + 1`
[ $J -eq 94 ] && J="1" && K=`expr $K + 1`
[ $K -eq 94 ] && K="1" && L=`expr $L + 1`
[ $L -eq 94 ] && L="1" && M=`expr $M + 1`
[ $M -eq 94 ] && M="1" && N=`expr $N + 1`
[ $N -eq 94 ] && N="1" && O=`expr $O + 1`
[ $O -eq 94 ] && O="1" && P=`expr $P + 1`
[ $P -eq 94 ] && P="1" && Q=`expr $Q + 1`
[ $Q -eq 94 ] && Q="1" && R=`expr $R + 1`
[ $R -eq 94 ] && R="1" && S=`expr $S + 1` 

if [ $S -ge 1 ]; then
echo "$(FIXED_S)$(FIXED_R)$(FIXED_Q)$(FIXED_P)$(FIXED_O)$(FIXED_N)$(FIXED_M)$(FIXED_L)$(FIXED_K)$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $R -ge 1 ]; then
echo "$(FIXED_R)$(FIXED_Q)$(FIXED_P)$(FIXED_O)$(FIXED_N)$(FIXED_M)$(FIXED_L)$(FIXED_K)$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $Q -ge 1 ]; then
echo "$(FIXED_Q)$(FIXED_P)$(FIXED_O)$(FIXED_N)$(FIXED_M)$(FIXED_L)$(FIXED_K)$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $P -ge 1 ]; then
echo "$(FIXED_P)$(FIXED_O)$(FIXED_N)$(FIXED_M)$(FIXED_L)$(FIXED_K)$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $O -ge 1 ]; then
echo "$(FIXED_O)$(FIXED_N)$(FIXED_M)$(FIXED_L)$(FIXED_K)$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $N -ge 1 ]; then
echo "$(FIXED_N)$(FIXED_M)$(FIXED_L)$(FIXED_K)$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $M -ge 1 ]; then
echo "$(FIXED_M)$(FIXED_L)$(FIXED_K)$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $L -ge 1 ]; then
echo "$(FIXED_L)$(FIXED_K)$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $K -ge 1 ]; then
echo "$(FIXED_K)$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $J -ge 1 ]; then
echo "$(FIXED_J)$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $I -ge 1 ]; then
echo "$(FIXED_I)$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $H -ge 1 ]; then
echo "$(FIXED_H)$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $G -ge 1 ]; then
echo "$(FIXED_G)$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $F -ge 1 ]; then
echo "$(FIXED_F)$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $E -ge 1 ]; then
echo "$(FIXED_E)$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $D -ge 1 ]; then
echo "$(FIXED_D)$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $C -ge 1 ]; then
echo "$(FIXED_C)$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $B -ge 1 ]; then
echo "$(FIXED_B)$(FIXED_A)$(SCROLL)"
elif [ $A -ge 1 ]; then
echo "$(FIXED_A)$(SCROLL)"
elif [ $A -eq 0 ]; then
echo "$(SCROLL)"
fi
done
}

PRINT

```~/characters is a text file with 93 ascii characters in it.

---

### Post by d3v1150m471c on 2010-09-06
this is much...much faster.

```

#!/bin/bash

[ -e ~/.scrypt ] || mkdir ~/.scrypt/.empty

export NUM="0"
export A="1"
export B="0"
export C="0"
export D="0"
export E="0"
export F="0"
export G="0"
export H="0"
export I="0"
export J="0"
export K="0"
export L="0"
export M="0"
export N="0"
export O="0"
export P="0"
export Q="0"


SCROLL() {
          head -$NUM ~/.scrypt/characters | tail -1
                                                   }

FIXED_A() {
           head -$A ~/.scrypt/characters | tail -1
                                                  }

FIXED_B() {
           head -$B ~/.scrypt/characters | tail -1
                                                  }

DICT_A() {
          head -$A ~/.scrypt/3 | tail -1
                                            }

DICT_B() {
          head -$B ~/.scrypt/4 | tail -1
                                            }

DICT_C() {
          head -$C ~/.scrypt/5 | tail -1
                                            }

DICT_D() {
          head -$D ~/.scrypt/6 | tail -1
                                            }

DICT_E() {
          head -$E ~/.scrypt/7 | tail -1
                                            }

DICT_F() {
          head -$F ~/.scrypt/8 | tail -1
                                            }

DICT_G() {
          head -$G ~/.scrypt/9 | tail -1
                                            }

DICT_H() {
          head -$H ~/.scrypt/10 | tail -1
                                            }

DICT_I() {
          head -$I ~/.scrypt/11 | tail -1
                                            }

DICT_J() {
          head -$J ~/.scrypt/12 | tail -1
                                            }

DICT_K() {
          head -$K ~/.scrypt/13 | tail -1
                                            }

DICT_L() {
          head -$L ~/.scrypt/14 | tail -1
                                            }

DICT_M() {
          head -$M ~/.scrypt/15 | tail -1
                                            }

DICT_N() {
          head -$N ~/.scrypt/16 | tail -1
                                            }

DICT_O() {
          head -$O ~/.scrypt/17 | tail -1
                                            }

DICT_P() {
          head -$P ~/.scrypt/18 | tail -1
                                            }

DICT_Q() {
          head -$Q ~/.scrypt/19 | tail -1
                                            }


###########################################################
# test bytes

BRUTE_0() {
while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && A=`expr $A + 1`

[ $A -eq 94 ] && A="1" && B=`expr $B + 1` && break

echo "$(FIXED_A)$(SCROLL)"

done
}

BRUTE_1() {

NUM="0"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && A=`expr $A + 1`

[ $A -eq 94 ] && A="1" && B=`expr $B + 1`
[ $B -eq 94 ] && break

echo "$(FIXED_B)$(FIXED_A)$(SCROLL)"

done
}

BRUTE_2() {

NUM="0"

COUNT=`wc -l ~/.scrypt/3 | sed 's%/home/$LOGNAME/.scrypt/3%%g'`

A="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && A=`expr $A + 1`
[ $A -gt $COUNT ] && NUM="0" && break

echo "$(DICT_A)$(SCROLL)"
done
}

BRUTE_3() {

NUM="0"

COUNT=`wc -l ~/.scrypt/4 | sed 's%/home/$LOGNAME/.scrypt/4%%g'`

B="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && B=`expr $B + 1`
[ $B -gt $COUNT ] && NUM="0" && break

echo "$(DICT_B)$(SCROLL)"
done
}

BRUTE_4() {

NUM="0"

COUNT=`wc -l ~/.scrypt/5 | sed 's%/home/$LOGNAME/.scrypt/5%%g'`

C="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && C=`expr $C + 1`
[ $C -gt $COUNT ] && NUM="0" && break

echo "$(DICT_C)$(SCROLL)"
done
}

BRUTE_5() {

NUM="0"

COUNT=`wc -l ~/.scrypt/6 | sed 's%/home/$LOGNAME/.scrypt/6%%g'`

D="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && D=`expr $D + 1`
[ $D -gt $COUNT ] && NUM="0" && break

echo "$(DICT_D)$(SCROLL)"
done
}

BRUTE_6() {

NUM="0"

COUNT=`wc -l ~/.scrypt/7 | sed 's%/home/$LOGNAME/.scrypt/7%%g'`

E="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && E=`expr $E + 1`
[ $E -gt $COUNT ] && NUM="0" && break

echo "$(DICT_E)$(SCROLL)"
done
}

BRUTE_7() {

NUM="0"

COUNT=`wc -l ~/.scrypt/8 | sed 's%/home/$LOGNAME/.scrypt/8%%g'`

F="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && F=`expr $F + 1`
[ $F -gt $COUNT ] && NUM="0" && break

echo "$(DICT_F)$(SCROLL)"
done
}


BRUTE_8() {

NUM="0"

COUNT=`wc -l ~/.scrypt/9 | sed 's%/home/$LOGNAME/.scrypt/9%%g'`

G="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && G=`expr $F + 1`
[ $G -gt $COUNT ] && NUM="0" && break

echo "$(DICT_G)$(SCROLL)"
done
}

BRUTE_9() {

NUM="0"

COUNT=`wc -l ~/.scrypt/10 | sed 's%/home/$LOGNAME/.scrypt/10%%g'`

H="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && H=`expr $H + 1`
[ $H -gt $COUNT ] && NUM="0" && break

echo "$(DICT_H)$(SCROLL)"
done
}

BRUTE_10() {

NUM="0"

COUNT=`wc -l ~/.scrypt/11 | sed 's%/home/$LOGNAME/.scrypt/11%%g'`

I="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && I=`expr $I + 1`
[ $I -gt $COUNT ] && NUM="0" && break

echo "$(DICT_I)$(SCROLL)"
done
}

BRUTE_11() {

NUM="0"

COUNT=`wc -l ~/.scrypt/12 | sed 's%/home/$LOGNAME/.scrypt/12%%g'`

J="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && J=`expr $J + 1`
[ $F -gt $COUNT ] && NUM="0" && break

echo "$(DICT_J)$(SCROLL)"
done
}

BRUTE_12() {

NUM="0"

COUNT=`wc -l ~/.scrypt/13 | sed 's%/home/$LOGNAME/.scrypt/13%%g'`

K="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && K=`expr $K + 1`
[ $K -gt $COUNT ] && NUM="0" && break

echo "$(DICT_K)$(SCROLL)"
done
}

BRUTE_13() {

NUM="0"

COUNT=`wc -l ~/.scrypt/14 | sed 's%/home/$LOGNAME/.scrypt/14%%g'`

L="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && L=`expr $L + 1`
[ $L -gt $COUNT ] && NUM="0" && break

echo "$(DICT_L)$(SCROLL)"
done
}

BRUTE_14() {

NUM="0"

COUNT=`wc -l ~/.scrypt/15 | sed 's%/home/$LOGNAME/.scrypt/15%%g'`

M="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && M=`expr $M + 1`
[ $M -gt $COUNT ] && NUM="0" && break

echo "$(DICT_M)$(SCROLL)"
done
}

BRUTE_15() {

NUM="0"

COUNT=`wc -l ~/.scrypt/16 | sed 's%/home/$LOGNAME/.scrypt/16%%g'`

N="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && N=`expr $N + 1`
[ $N -gt $COUNT ] && NUM="0" && break

echo "$(DICT_N)$(SCROLL)"
done
}

BRUTE_16() {

NUM="0"

COUNT=`wc -l ~/.scrypt/17 | sed 's%/home/$LOGNAME/.scrypt/17%%g'`

O="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && O=`expr $O + 1`
[ $O -gt $COUNT ] && NUM="0" && break

echo "$(DICT_O)$(SCROLL)"
done
}

BRUTE_17() {

NUM="0"

COUNT=`wc -l ~/.scrypt/18 | sed 's%/home/$LOGNAME/.scrypt/18%%g'`

P="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && P=`expr $P + 1`
[ $P -gt $COUNT ] && NUM="0" && break

echo "$(DICT_P)$(SCROLL)"
done
}

BRUTE_18() {

NUM="0"

COUNT=`wc -l ~/.scrypt/19 | sed 's%/home/$LOGNAME/.scrypt/19%%g'`

Q="1"

while NUM=`expr $NUM + 1`;do

[ $NUM -eq 94 ] && NUM="1" && Q=`expr $F + 1`
[ $Q -gt $COUNT ] && NUM="0" && break

echo "$(DICT_Q)$(SCROLL)"
done
}


cd ~/.scrypt/.empty

BRUTE_0 >~/.scrypt/2
BRUTE_1 >~/.scrypt/3
BRUTE_2 >~/.scrypt/4
BRUTE_3 >~/.scrypt/5
BRUTE_4 >~/.scrypt/6
BRUTE_5 >~/.scrypt/7
BRUTE_6 >~/.scrypt/8
BRUTE_7 >~/.scrypt/9
BRUTE_8 >~/.scrypt/10
BRUTE_9 >~/.scrypt/11
BRUTE_10 >~/.scrypt/12
BRUTE_11 >~/.scrypt/13
BRUTE_12 >~/.scrypt/14
BRUTE_13 >~/.scrypt/15
BRUTE_14 >~/.scrypt/16
BRUTE_15 >~/.scrypt/17
BRUTE_16 >~/.scrypt/18
BRUTE_17 >~/.scrypt/19
BRUTE_18 >~/.scrypt/20


```

---

