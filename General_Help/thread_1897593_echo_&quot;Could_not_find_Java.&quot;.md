---
title: "echo &quot;Could not find Java.&quot;"
date: 2011-12-19
forum: General Help
---

### Post by sinbowden on 2011-12-19
I installed, openjdk-6-jdk and I get this msg when I try to execute an install. 

if ! java -version > /dev/null 2>&1
then
echo "Could not find Java."
echo "You must have Java installed and in your path."
exit
fi

relativePathToGame=`dirname $0`
cd $relativePathToGame


java -Xmx512m -cp bin/patch.jar:bin/triplea.jar games.strategy.engine.framework.GameRunner

---

