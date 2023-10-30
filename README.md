# **GrafikaProjektTemplate**

Premake5 je jednostavni alat za automatsko podešavanje razvojne okoline, skripta je napisana u lua skriptnom jeziku. Ovi alat nam omogućuje da konfiguriramo našu okolinu (tip projekta, platformu, folder binarnih datotetka, linkamo librarye, ... ) u premake5.lua skripti.\
Nakon konfiguracije, možemo pokreniti premake5 s argumentom željene okoline, te će nam generirati traženu okolinu. Generalno ovakav alat nam omogućuje, da možemo generirati okolinu za naš projekt, na različitim OS-ovima, s različitim libraryovima te različite i za različite razvojne okoline (ne mora biti visual studio), [vidi dokumentaciju za premake](https://premake.github.io/docs/Using-Premake).\
U praksi se koriste ostali i kompleksniji softveri za automatizirano postavljanje, testirianje, buildanje, instaliranje... Neki od tih su CMake, Scons... 

#### **NAPOMENA:** Zasad sam podesia premake samo za visual studio '17, '19 i '22 i to na windowsima. 

### **Struktura** **projekta**

Projekt *GrafikaLabovi_ImePrezime* se nalazi u istoimenom folderu, te se sastoji od dva foldera *res* i *src*.\
U resource folderu se nalaze modeli (obj fajlovi), shaderi i teksture te su svi organizirani u svoje foldere.\
U source folderu se nalazi kodovi, također organzirani po folderima, osim *main.cpp* i *glad.c*. U folderu *vendor* se nalaze alati koji nisu naši, a koristit ćemo ih.

### **Pokretanje** **na** **WINDOWSIMA**
#### 1. Klonirajte ili skinite zip ovog repozitorija. 
#### 2. U premake5.lua prominite linije 1., 7. i 8. u ime kako želite. 
#### 3. Ako ste minjali ime, **obavezno** prominite ime foldera *GrafikaLabovi_ImePrezime* u isto.
#### 4. Otvorite tekstualnim editorom batch skriptu *GenerateProject.bat*, ovisno o vašoj verziji visual studia promijenite argument u *vs2017*, *vs2019*, *vs2022*.
#### 5. Sada pokrenite istu batch skriptu. 
#### 6. Generirat će vam se visual studio solution.
#### 7. Otvorite visual studio solution, i u solution exploreru odaberite *Show All Files* ikonu, da bi vam se prikazale sve datoteke i pravi folderi projekta, [vidi sliku](https://i.stack.imgur.com/NmkhK.png).
#### **NAPOMENA:** Neće vam raditi, ako u pathu ili u imenu imate č,ć,đ,š,ž i sl.

### **Za** **ostale**
Vi koji ste podesili na macOS-u ili ste podesili sami visual studio, radite i dalje u toj okolini (ili ako želite podesite novu okolinu za ovu vježbu), sve šta trebate napravite uvalite sve iz *src-a* u folder projekta (pazite da vam *main.cpp* ne overwrita vaš main, i da vam svi .cpp, .c, .h i .hpp budu *includani* u projekt).\
Također uvalite sve iz *res* foldera u vaš projekt, generalno svi resursi fajlovi bi trebali biti *excludani* iz projekta, ali jedino vam .obj stvoriti problem ako su *includani* tako da ih *excludate*.\
Sad sami organzirajte svoj projekt, a moj vam je savjet da stavite strukturu kao i ja. Ali svakako ćete morati u kodu minjati putanje (path), te ih prilagoditi vašim, ja sam to postavio u premake skripti.\
#### Na primjer:

```cpp
#include "Window.h"
#include "Renderer.h"
#include "Model.h"
#include "Shader.h"
#include "Texture.h"

#include "glm/glm.hpp"
```
 #### promijeniti (ako imate src folder, ovo je **primjer**) u: 
 ```cpp
#include "src/Window/Window.h"
#include "src/Renderer/Renderer.h"
#include "src/Model/Model.h"
#include "src/Shader/Shader.h"
#include "src/Texture/Texture.h"

#include "src/vendor/glm/glm.hpp"
```

#### za resurse nisam kratio path u premaku. Root patha vam je folder projekta.


### **GLSL** **ekstenzija**
Za shadere, koji će vam biti u zasebnim fajlovima, ako nećete koristit ekstenziju onda vam je nebitna ekstenzija (može i obični .txt) bitno da je u tekstualnom obliku i da se može pročitati. Ovi shaderi su jako jednostavni, i ako falijete neki tipfeler/sintaksu u konzoli aplikacije će vam OpenGL vratiti syntax error i u kojem shader te mjesto greške. Tako da vam i ekstenzija neće trebati.\

Ja koristim [ovu verziju](https://marketplace.visualstudio.com/items?itemName=DanielScherzer.GLSL2022) ekstenzije za highlightanje GLSLa u vs2019. Ekstenzije u vs-u se instaliraju [ovako](https://learn.microsoft.com/en-us/visualstudio/ide/finding-and-using-visual-studio-extensions?view=vs-2022).\
Da bi ova ekstenzija (mislim da i ostale) prepoznaju GLSL kod, shader mora imati ekstenziju *.glsl*. Možete koristit i neki drugi editor (npr. VS code) i u tom editoru naći ekstenziju\ 

### Ostalo
#### Ove upute 200% imaju tipfelera i gramatičkih grešaka (ako je ko voljan ispravljat neka forka i pull requesta) i sl. Uopće ih nisan pročita drugi put.
#### Za vježbu sve od c++ pišete u mainu(ako radite po templatu), a za svaki zadačić napravite novi set shadera (triba vam i vertex i fragment po zad, nazovite npr. zad3Vertex.glsl i zad3.Fragment.glsl ili bolje smislite).
#### Također ovo je moja abstrakcija OpenGLa, i nisan puno potrošia vrimena, tako da... 
#### Za uniforme pozivate ih priko metoda shader klase, pogledajte Shader.h. 
#### Isto tako upute nisu baš najbolje napisane, pa mi se slobodno javite mailon, može i wapp (samo se predstavite). 