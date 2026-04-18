# 03. Architecture

## Подход
Приложение разрабатывается как Android-приложение на Kotlin без backend-сервера.

Архитектурный стиль:
- MVVM
- разделение на data / domain / presentation
- Jetpack Compose для UI

## Основные слои

### Presentation
Содержит:
- экраны
- composable-компоненты
- navigation
- ViewModel
- ui state

### Domain
Содержит:
- use cases
- бизнес-правила
- абстракции репозиториев

### Data
Содержит:
- API-клиенты
- DTO
- мапперы
- локальное хранение
- repository implementation

## Модули MVP

### 1. Onboarding
- приветствие
- настройка PIN
- включение биометрии
- первичная настройка профиля

### 2. Auth / Security
- проверка PIN
- биометрия
- экран разблокировки

### 3. Profile
- пол
- возрастной диапазон
- аватар
- локальное хранение данных профиля

### 4. Location
- получение текущей локации
- геокодирование / reverse geocoding
- ручной выбор города

### 5. Weather
- загрузка текущей погоды
- загрузка почасового прогноза
- загрузка недельного прогноза

### 6. Air Quality
- загрузка текущего показателя качества воздуха
- маппинг в понятные UI-категории

## Локальное хранение
Для MVP рекомендуется:
- DataStore для настроек, PIN-флагов, города, профиля
- при необходимости Room позже, если появится история или кэш-структуры сложнее

## Сетевой слой
- Retrofit
- OkHttp
- Coroutines
- JSON parser

## Изображения
- Coil для загрузки аватара из URI
- сохранение URI/пути на устройстве

## Навигация
- Navigation Compose

Основные экраны:
- Splash / Launch
- PIN Unlock
- Onboarding
- Profile Setup
- Main Weather Screen
- City Selection

## Рекомендуемый стек библиотек
- Jetpack Compose
- Material 3
- Navigation Compose
- Lifecycle ViewModel
- Kotlin Coroutines
- Retrofit
- OkHttp
- Kotlinx Serialization or Moshi
- DataStore
- Biometric
- Play Services Location
- Coil

## Базовая структура пакетов

com.example.airqualityapp
- data
  - remote
  - local
  - repository
  - mapper
  - model
- domain
  - model
  - repository
  - usecase
- presentation
  - navigation
  - onboarding
  - auth
  - main
  - profile
  - location
  - components
  - theme
- util
