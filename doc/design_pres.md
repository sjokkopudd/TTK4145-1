# Elevator Design Presentation

Før vi setter i gang, kan det være nyttig å vite at vi har valgt å gjøre vårt design i Elixir, fordi det virket som en god utfordring og fordi Elixir har mye interessant innebygd funksjonalitet.
Presentasjonen er delt opp i fire deler:
1. Oversikt over våre moduler, med et medfølgende klassediagram
2. En demonstrasjon av en "happy path" med et sekvensdiagram
3. En diskusjon av potensielle feil og feilhåndtering
4. Et sekvensdiagram som ser på en feilhåndtering og recovery

### 1. Moduler
Dette klassediagrammet viser modulene vi har valgt, samt utvalgte metoder som viser hvordan de kommuniserer med hverandre. 
Først er det verdt å nevne at vi følger elixirs navnekonvensjon, moduler er CamelCase, alt annet er snake_case.
Vi leser diagrammet fra øverst til høyre:
 - Først har vi den gitte DriverInterfacen, som vi ikke har endret på.
 - Modulen "Poller" gir et ekstra abstraksjonslag, ved å loope og sende knappetrykk som meldinger og sende medlinger om etasje-endring til statemachinen.
 - StateMachine har strukten direction og floor, mottar kommandoer og bekrefter gjennomførelse
 - OrderHandler har en ordrematrise, og kan regne ut en kostnadsfunksjon for en heis i en gitt tilstand, der heisen med den laveste costen blir sendt ordren. Orderen kan være sendt og usendt.
 - NetworkHandler har ansvaret for oppstart av nettverket, og har også mulighet til å fange opp noder som taper forbindelse og restarte noder eller nettverk 
 - WatchDog tar seg av feil som ikke er nettverksrelaterte i den forstand at de lar seg løse av NetworkModule, eksempel på dette er ordre som ikke blir gjennomført p.g.a motorstopp.  

### 2. Happy path
Her er et eksempel på oppstart 
Under oppstart brukes NetworkHandler.init_nodes() der UDP-broadcast av IP-addresse og initialisering av prosesser, lagring av PID. Dere

### 3. Feilhåndtering
!!!!merging error modes!!!!
backups

### 4. Bad path