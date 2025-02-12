# skolelinux-dugnad-for-Ukraina

Depot for skript, etc som vil gjøre installasjon av brukte bærbare datamaskiner mer effektivt

Formål med preseeden er å gjøre det raskere å installere uten at man må svare på mange spørsmål

Preseed-mulighetene i Debian er beskrevet i https://www.debian.org/releases/stable/amd64/apb.en.html .

1) DONE: Vi skal ha kde som standard skrivebord
2) DONE: Vi skal ha Frittstående installasjon
3) ToDo: Vi skal ha alt installert under /
4) ToDo: Vi vil ha vekk lvm og kjøre alt "rett på jernet"
5) DONE: Vi skal bruke dette speilet: http://deb.debian.org/debian
6) DONE: Vi skal ha med main non-free-firmware contrib non-free
7) DONE: pakken firmware-b43-installer bør installeres for maskiner som trenger den.
8) DONE: pakken task-ukrainian-desktop er med
9) PARTLY DONE: kiosk-modus må settes opp, slik at maskinen starter rett opp i skrivebord
   uten noe innlogging og at maskinen logger inn igjen om man logger ut
10) DONE: oppdatere systemet til nyeste versjon med sudo apt update && sudo apt dist-upgrade -y (eller tilsvarende) før systemet starter opp om mulig
11) Se https://wiki.nuug.no/skolelinux for detaljer rundt passord

Implementert i preeseed-skolelinux.cfg:

 1) KDE skrivebord
 2) Frittstående installasjon
 5) APT satt opp med http://deb.debian.org/debian
 6) Aktiverte komponenter: main contrib non-free non-free-firmware1
 8) Pakken task-ukrainian-desktop installeres, som del av ukranisk forvalgt oppsett.
 9) Pakken sddm settes i kiosk-modus med bruker ukraina
 10) Hardcoded passord for bruker ukraina med sudo-tilgang.  Intet root-passord.

Punktene 3-4 er endel jobb og ikke forsøkt i denne omgang.
Punkt 7 krever bruk av annen ISO (for eksempel netinst-ISO), som bruker Internett
under installasjonen for å kunne laste ned boardcom-binærblob.

Tastatur settes opp for både ukrainsk og amerikansk.  Trykk på Alt+Shift bytter mellom
tastaturutleggene.

For å aktivere, trykk 'tab' på oppstartmenyen fra installasjonsmediet, og erstatt
desktop=xfce med

  locale=uk_UA.UTF-8 keymap=ua keyboard-configuration/toggle=Alt+Shift url=https://people.skolelinux.org/pere/preseed-ukraina.cfg

Katalogen debconf-selections inneholder resultatet fra kjøring av

  debconf-get-selection > debconf-get-selection.txt
  debconf-get-selection --installer > debconf-get-selection-installer.txt

fra et system installert i henhold til oppskrift på wiki 2023-10-18.  Disse filene
er nyttige når en skal utvide preseed-oppsettet.
