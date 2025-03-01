<p align="center">
  <a href="../README.md">English</a> | <a href="./README_chs.md">中文</a> | Русский | <a href="./README_jpn.md">日本 語</a> | <a href="./README_ukr.md">Українська</a> | <a href="./README_kor.md">한국어</a> | <a href="/docs/README_cze.md">Česky</a> | <a href="/docs/README_gr.md">Ελληνικά</a>  <br>
    <sub>Внимание: файлы "О проекте" поддерживаются переводчиками и могут время от времени не соответствовать текущей версии. Для новейшей информации полагайтесь на англоязычный вариант.</sub>
</p>
<h1 align="center">
  Galaxy Buds Client
  <br>
</h1>
<h4 align="center">Неофициальный менеджер для Buds, Buds+, Buds Live и Buds Pro</h4>
<p align="center">
  <a href="https://github.com/ThePBone/GalaxyBudsClient/releases">
    <img alt="Кол-во скачиваний с GitHub" src="https://img.shields.io/github/downloads/thepbone/galaxybudsclient/total">
  </a>
  <a href="https://github.com/ThePBone/GalaxyBudsClient/releases">
   <img alt="Последняя версия на GitHub" src="https://img.shields.io/github/v/release/thepbone/galaxybudsclient">
  </a>
  <a href="https://github.com/ThePBone/GalaxyBudsClient/blob/master/LICENSE">
      <img alt="Лицензия" src="https://img.shields.io/github/license/thepbone/galaxybudsclient">
  </a>
  <a href="https://github.com/ThePBone/GalaxyBudsClient/releases">
    <img alt="Платформа" src="https://img.shields.io/badge/platform-Windows-yellowgreen">
  </a>
</p>
<p align="center">
  <a href="#основные-возможности">Основные возможности</a> •
  <a href="#скачать">Скачать</a> •
  <a href="#как-это-работает">Как это работает</a> •
  <a href="#внести-вклад">Внести вклад</a> •
  <a href="#участники">Участники</a> •
  <a href="#лицензия">Лицензия</a>
</p>

<p align="center">
    <a href="https://ko-fi.com/H2H83E5J3"><img alt="Screenshot" src="https://ko-fi.com/img/githubbutton_sm.svg"></a>
</p>

<p align="center">
    <a href="#"><img alt="Screenshot" src="https://github.com/ThePBone/GalaxyBudsClient/blob/master/screenshots/screencap.gif"></a>
</p>

## Основные возможности

Настраивайте и управляйте любыми устройствами Samsung Galaxy Buds и интегрируйте их в свой компьютер.

Помимо стандартных функций, известных из официального приложения для Android, этот проект поможет вам раскрыть весь потенциал ваших наушников и реализует новые функции, такие как:

* Подробная статистика батареи
* Диагностика и заводское самотестирование
* Множество скрытой отладочной информации
* Настраиваемые действия удержания сенсорной панели
* Установка прошивки, даунгрейдинг (Buds+, Buds Pro)
* и многое другое...

## Скачать

Загрузите файлы для Windows в разделе [выпусков (releases)](https://github.com/ThePBone/GalaxyBudsClient/releases). Пожалуйста, прочтите примечания к выпуску перед установкой.

<p align="center">
    <a href="https://github.com/ThePBone/GalaxyBudsClient/releases"><img alt="Download" src="https://github.com/ThePBone/GalaxyBudsClient/blob/master/screenshots/download.png"></a>
</p>
Выпуск для Windows теперь можно установить через Менеджер Пакетов Windows (WinGet)

```
winget install ThePBone.GalaxyBudsClient
```

#### Arch Linux (AUR)

Пользователи Arch Linux могут загрузить независимый (dependencyless) [AUR пакет](https://aur.archlinux.org/packages/galaxybudsclient/):

```
yay -S galaxybudsclient
```

## Как это работает

Чтобы использовать беспроводную связь Bluetooth, устройство должно уметь интерпретировать некоторые профили Bluetooth, которые являются определениями возможных применений устройства, и обозначать общее поведение, которое устройства с поддержкой Bluetooth используют для связи с другими устройствами.

Galaxy Buds определяют два профиля Bluetooth: A2DP (Advanced Audio Distribution Profile) для потоковой передачи / управления аудио и SPP (Serial Port Profile) для передачи потока бинарных данных. Производители часто используют этот профиль (который основан на протоколе RFCOMM) для обмена данными конфигурации, выполнения обновлений прошивки или отправки других команд на устройство Bluetooth.

Несмотря на то, что профиль A2DP стандартизирован и задокументирован, формат фактических бинарных данных, которыми обменивается этот протокол RFCOMM, обычно не документируется и является собственностью компании производителя.

Чтобы реконструировать этот формат данных, я начал с анализа структуры двоичного потока, отправляемого наушниками. Позже я также дизассемблировал официальные приложения Galaxy Buds для Android, чтобы лучше понять внутреннюю работу этих устройств. Работая над этим, я документировал свои мысли в журнале. Пускай их и не очень удобно читать, я прикладываю их ниже. Имейте в виду, что я не стал записывать каждую деталь. Проверьте исходный код, чтобы получить более подробную информацию о структуре протокола.

<p align="center">
  <a href="https://github.com/ThePBone/GalaxyBudsClient/blob/master/GalaxyBudsRFCommProtocol.md">Galaxy Buds (2019) Notes</a> •
  <a href="https://github.com/ThePBone/GalaxyBudsClient/blob/master/Galaxy%20Buds%20Plus%20RFComm%20Protocol%20Notes.md">Galaxy Buds Plus Notes</a>
</p>

Присмотревшись к Galaxy Buds Plus, я также заметил некоторые необычные функции, такие как режим отладки прошивки, неиспользуемый режим сопряжения и дампер адресов Bluetooth. Я задокументировал эти результаты здесь:

<p align="center">
  <a href="https://github.com/ThePBone/GalaxyBudsClient/blob/master/GalaxyBudsPlus_HiddenDebugFeatures.md">Galaxy Buds Plus: Unusual features</a>
</p>

В настоящее время я занимаюсь модификацией и реверс-инжинирингом прошивки для Buds+. На момент написания у меня есть два инструмента для извлечения и анализа с помощью официальных двоичных файлов прошивки. Посмотрите их здесь:

<p align="center">
  <a href="https://github.com/ThePBone/GalaxyBudsFirmwareDownloader">Firmware Downloader</a> •
  <a href="https://github.com/ThePBone/GalaxyBudsFirmwareExtractor">Firmware Extractor</a>
</p>
Получайте данные про отслеживание положения головы в режиме реального времени от ваших Buds Pro используя этот скрипт: [ThePBone/BudsPro-Headtracking](https://github.com/ThePBone/BudsPro-Headtracking)

## Внести вклад

Предложения функций, отчеты об ошибках и запросы на слияние (pull request) любого рода всегда приветствуются.

Если вы хотите сообщить об ошибках или предложить свои идеи для этого проекта, вы можете [открыть проблему](https://github.com/ThePBone/GalaxyBudsClient/issues/new/choose) с подходящим шаблоном. [Посетите нашу вики](https://github.com/ThePBone/GalaxyBudsClient/wiki/2.-How-to-submit-issues) для получения подробного объяснения.

Если вы планируете помочь нам в переводе этого приложения, [просмотрите инструкции в нашей вики](https://github.com/ThePBone/GalaxyBudsClient/wiki/3.-How-to-help-with-translations). Знания в области программирования не требуются, вы можете протестировать свои переводы без установки каких-либо инструментов разработки перед отправкой запроса на слияние.

Если вы хотите внести свой собственный код, вы можете просто отправить простой запрос на слияние с объяснением ваших изменений. Для более крупных и сложных вкладов было бы неплохо, если бы вы могли открыть проблему (issue) (или написать мне в Telegram [@thepbone](https://t.me/thepbone)), прежде чем начинать работу над ним.

## Участники

#### Соучастники

* [@ArthurWolfhound](https://github.com/ArthurWolfhound) - Шаблоны уведомлений о проблемах, вики и переводы
* [@AndriesK](https://github.com/AndriesK) - Исправление ошибок при работе с Buds Live
* [@TheLastFrame](https://github.com/TheLastFrame) - Иконки для Buds Pro
* [@githubcatw](https://github.com/githubcatw) - Програмная основа диалога подключения
* [@GaryGadget9](https://github.com/GaryGadget9) - Пакет для Менеджера Пакетов Windows (WinGet)

#### Переводчики

* [@ArthurWolfhound](https://github.com/ArthurWolfhound) - Русский и Украинский переводы
* [@PlasticBrain](https://github.com/fhalfkg) - Корейский и Японский переводы
* [@cozyplanes](https://github.com/cozyplanes) - Корейский перевод
* [@erenbektas](https://github.com/erenbektas) - Турецкий перевод
* [@kakkk](https://github.com/kakkk) , [@KevinZonda](https://github.com/KevinZonda), [@ssenkrad](https://github.com/ssenkrad) и [@pseudor](https://github.com/pseudor) - Китайский перевод
* [@efrenbg1](https://github.com/efrenbg1) и Andrew Gonza - Испанский перевод
* [@giovankabisano](https://github.com/giovankabisano) - Индонезийский перевод
* [@lucasskluser](https://github.com/lucasskluser) - Португальский перевод
* [@alb-p](https://github.com/alb-p), [@mario-donnarumma](https://github.com/mario-donnarumma) - Итальянский перевод
* [@Buashei](https://github.com/Buashei) - Польский перевод
* [@KatJillianne](https://github.com/KatJillianne) - Вьетнамский перевод
* [@joskaja](https://github.com/joskaja) and [@Joedmin](https://github.com/Joedmin) - Чешский перевод
* [@TheLastFrame](https://github.com/TheLastFrame), [@ThePBone](https://github.com/ThePBone) - Немецкий перевод
* [@nikossyr](https://github.com/nikossyr) - Греческий перевод
* [@grigorem](https://github.com/grigorem) - Румынский перевод
* [@tretre91](https://github.com/tretre91) - Французский перевод

## Лицензия

Этот проект распространяется по лицензии [GPLv3](../LICENSE). Он никоим образом не связан с Samsung и не контролируется ею.

```
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, 
INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. 
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, 
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR 
THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```
