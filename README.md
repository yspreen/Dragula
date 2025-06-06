# 🧛 Dragula

**Dragula** is a delightfully flexible and smooth drag-and-drop Swift package for building reorderable interfaces in SwiftUI. Inspired by Dracula's ability to move swiftly through the night (and by your need to reorder views), Dragula gives your lists and grids superpowers — with minimal code and maximum polish.

---

## ✨ Features

- 🔀 Reorder items within a list or across sections
- 🧱 Sectioned and unsectioned layouts
- ↔️ Horizontal and vertical scroll support
- 🍞 Drop previews, haptics, and corner radius customization
- 🧩 UIKit-backed for pixel-perfect drag interaction

---

## 🧰 Requirements

- iOS 16+
- Swift 5.8+
- Xcode 15+

---

## 🚀 Getting Started

### 1. Import the package

Add Dragula via Swift Package Manager:

```
https://github.com/mufasayc/Dragula.git
```

### 2. Define Your Models

```swift
struct MyItem: DragulaItem {
    let id = UUID()
    let title: String
}

struct MySection: DragulaSection {
    let id = UUID()
    let title: String
    var items: [MyItem]
}
```

---

### 3. Use `DragulaView` (for flat lists)

```swift
DragulaView(items: $myItems) { item in
    Text(item.title)
} dropView: { item in
    Color.gray
} dropCompleted: {
    // save the new order to db
}
```

---

### 4. Use `DragulaSectionedView` (for sectioned lists)

```swift
DragulaSectionedView(sections: $sections) { section in
    Text(section.title)
} card: { item in
    Text(item.title)
} dropView: { item in
    Color.secondary
} dropCompleted: {
    // save the new order to db
}
```

---

## 🎛 Environment Options

Customize the drag preview appearance:

```swift
.environment(\.dragPreviewCornerRadius, 12)
```

---

## 📦 Example

Check out `ContentView.swift` in the demo project to see:

- Vertical sectioned drag and drop
- Flat list reordering
- Horizontal drag views with scrolling

---

## 🧙‍♂️ Name Origin

> *“I want to drag your views...”*
> — Count Dragula

---

## 🧑‍💻 Author

Built by [Mustafa Yusuf](https://x.com/mufasayc)

---

## 🐞 Known Issues

- A slight drag doesn't trigger `cancel`, which appears to be a UIKit bug. A fix is in progress.
- On Mac Catalyst, `cancel` is not called in `UIDragDelegate` for some reason — investigating this.
- Plan to introduce a unified initializer in `DragulaView` to support both sectioned and flat lists.
- Support for accepting drops containing items not already in the list will be added soon.

## 📄 License

MIT License
