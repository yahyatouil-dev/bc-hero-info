# ⛉ BC HERO — Superpowers for Business Central

> **BC HERO** is a Visual Studio Code extension built for Business Central AL developers. It brings together seven powerful, purpose-built tools under one unified interface — from scaffolding new projects and generating AL code, to exploring live APIs, managing translations, and visualising your schema and object dependencies.

---

## Table of Contents

- [Features Overview](#features-overview)
- [Commands Reference](#commands-reference)
- [Quick Project Setup](#1-quick-project-setup)
- [AL Object Creator](#2-al-object-creator)
- [JSON → AL Generator](#3-json--al-generator)
- [API Explorer](#4-api-explorer)
- [Translation Assistant](#5-translation-assistant)
- [Schema Viewer](#6-schema-viewer)
- [Dependency Graph](#7-dependency-graph)
- [Getting Started](#getting-started)
- [Tips & Shortcuts](#tips--shortcuts)

---

## Features Overview

| Tool | Command | Description |
|---|---|---|
| 🗂️ Quick Project Setup | `BC HERO: Open Quick Project Setup` | Scaffold a standard AL folder structure in seconds |
| 🧱 AL Object Creator | `BC HERO: Open AL Object Creator` | Generate AL objects with a guided form and batch queue |
| 🔄 JSON → AL Generator | `BC HERO: Open JSON2AL Generator` | Turn any JSON payload into ready-to-use AL code |
| 🔌 API Explorer | `BC HERO: Open API Explorer` | Browse, test, and inspect your BC API endpoints live |
| 🌍 Translation Assistant | `BC HERO: Open Translation Assistant` | Manage XLIFF translation files with a visual editor |
| 🗄️ Schema Viewer | `BC HERO: Open Schema Viewer` | Explore table schemas, fields, keys, and relationships |
| 🕸️ Dependency Graph | `BC HERO: Open Dependency Graph` | Visualise object dependencies across your workspace |

---

## Commands Reference

All commands are available from the **Command Palette** (`Ctrl+Shift+P` / `Cmd+Shift+P`). Type `BC HERO` to filter the list.

```
BC HERO: Open Quick Project Setup
BC HERO: Open AL Object Creator
BC HERO: Open JSON2AL Generator
BC HERO: Open API Explorer
BC HERO: Open Translation Assistant
BC HERO: Open Schema Viewer
BC HERO: Open Dependency Graph
```

---

## 1. Quick Project Setup

**Command:** `BC HERO: Open Quick Project Setup`

Instantly scaffold a clean, professional AL project folder structure without leaving VS Code. Instead of manually creating directories, select the components your project needs and BC HERO creates them all in one click.

![Quick Project Setup](images/QuickProjectSetup.png)

### How to Use

1. Open the panel via the Command Palette.
2. Set the **Source Root Folder** — the base folder where all subdirectories will be created (e.g. `src`). The resolved path is shown in real time beneath the input.
3. From the component list, **check the folders** you need. Use **Select All** to enable every component, or tick them individually.
4. Watch the **live preview tree** on the right update as you make selections — you always know exactly what will be created before committing.
5. Click **Create Folders** to generate the structure. A results panel confirms each folder created.

### Available Components

BC HERO can scaffold any combination of the following standard AL folders:

`Tables` · `Pages` · `Reports` · `XMLPorts` · `Queries` · `Codeunits` · `ControlAddIns` · `PageExtensions` · `TableExtensions` · `Profiles` · `PageCustomizations` · `Enums` · `EnumExtensions` · `DotNetPackages` · `Interfaces` · `ReportExtensions`

### Features at a Glance

- **Live preview tree** — see the resulting folder structure before creating anything.
- **Resolved path hint** — the full absolute path to your source root is shown dynamically as you type.
- **Batch creation** — all selected folders are created in a single operation.
- **Reset** — clears all selections and restores defaults instantly.

---

## 2. AL Object Creator

**Command:** `BC HERO: Open AL Object Creator`

A guided, form-based wizard for generating AL object files. Configure each object's type, ID, name, fields, and destination — then queue multiple objects and create them all at once.

![AL Object Creator](images/ALObjectCreator.png)

### How to Use

1. Open the panel and select an **Object Type** from the dropdown (16 types supported).
2. Fill in the common fields:
   - **Object ID** — auto-suggested based on the highest existing ID in your workspace for the chosen type.
   - **Name** — the AL object name.
   - **Caption** — defaults to the name if left blank.
3. Fill in the **type-specific fields** that appear below (e.g. fields for a Table, source table for a Page, values for an Enum).
4. Set the **Destination Folder** where the `.al` file should be saved. Click **Browse** to pick a folder visually.
5. Click **+ Add Object** (or press `Ctrl+Enter`) to add the object to the **Batch Queue** on the left.
6. Repeat for additional objects. Each queued item shows its name, type badge, and assigned ID.
7. Click **✓ Done** to create all queued objects at once. A results panel lists every file created.

### Supported Object Types

| Type | Details |
|---|---|
| Table | Fields, data types, lengths, captions |
| Page | Page type (Card, List, API…), source table, layout fields |
| Report | Data item, columns, request page toggle |
| XML Port | Direction, format, source table, field names |
| Query | Normal or API query, data items, columns |
| Codeunit | Single-instance toggle, procedure stubs |
| Control Add-in | Scripts, stylesheets, dimensions |
| Page Extension | Extends an existing page, adds fields and actions |
| Table Extension | Extends an existing table, adds fields |
| Profile | Profile ID, role center, enabled/promoted flags |
| Page Customization | Customizes an existing page |
| Enum | Values with IDs and captions, extensible flag |
| Enum Extension | Extends an existing enum with new values |
| .NET Package | Assembly, version, culture, public key, type aliases |
| Interface | Procedure signatures |
| Report Extension | Extends an existing report with columns |

### Features at a Glance

- **Smart ID suggestion** — the Object ID field is automatically pre-filled with the next available ID for the selected type, accounting for both existing workspace objects and objects already in the batch queue.
- **Batch queue** — build a list of objects before generating, then create them all in one go.
- **Per-item removal** — click the ✕ on any queued item to remove it without clearing the rest.
- **Rescan IDs** — click the refresh icon in the toolbar to re-scan the workspace for the latest used object IDs.
- **`Ctrl+Enter` shortcut** — adds the current form state to the queue without reaching for the mouse.

---

## 3. JSON → AL Generator

**Command:** `BC HERO: Open JSON2AL Generator`

Drop any JSON file onto BC HERO and receive fully structured AL code — tables, pages, or XMLports — with fields, types, and captions inferred automatically from the JSON data.

![AL JSON To AL Generator](images/JSON2AL.png)

### How to Use

1. Open the panel. The left side shows a **drop zone**.
2. **Drag and drop** a `.json` file onto the drop zone, or click **Browse** to select one. OData responses (`{ "value": [...] }`) and plain JSON arrays or objects are all supported.
3. BC HERO analyses the JSON and lists all detected **fields** in the left panel, showing each field's inferred AL type and a sample value from the data.
4. Use the checkboxes to **select or deselect** individual fields. Use **All** / **None** buttons to toggle everything at once.
5. Choose an **object type** from the tabs along the top: **Table**, **Page List**, **Page Card**, or **XMLport**.
6. Fill in the **configuration panel** (object number, name, source table, etc.) for the chosen type.
7. In the **field configuration table**, fine-tune each field: edit the AL name, change the data type, and adjust the length for `Text` or `Code` fields.
8. Click **▶ Generate AL Code**. The right panel displays syntax-highlighted AL code ready to use.
9. Click **Copy** to copy the code to your clipboard, or **Create .al File** to save it directly into a selected folder in your workspace.

### Field Type Inference

BC HERO maps JSON value types to sensible AL defaults:

| JSON Type | Default AL Type |
|---|---|
| String | `Text[100]` |
| Number | `Decimal` or `Integer` |
| Boolean | `Boolean` |
| Null | `Text[100]` |
| Object / Array | `Text[250]` |

All inferred types can be overridden in the field configuration table before generating.

### Features at a Glance

- **Drag-and-drop** JSON loading — works anywhere on the window.
- **OData support** — automatically unwraps `{ "value": [...] }` response envelopes.
- **Live AL syntax highlighting** — keywords, strings, numbers, and comments are colour-coded in the preview pane.
- **Per-field customisation** — rename fields, change types, and adjust lengths without editing the generated code.
- **Direct file creation** — generates a `.al` file with a sensible suggested filename.

---

## 4. API Explorer

**Command:** `BC HERO: Open API Explorer`

A full-featured HTTP client built specifically for Business Central APIs. Browse API endpoints discovered in your workspace, configure authentication, build requests with query parameters, and inspect responses — all inside VS Code.

![API Explorer](images/APIExplorer-1.png)

<br>

![API Explorer](images/APIExplorer-2.png)

### How to Use

#### Connect to Your Environment

1. Click the **connection pill** (top-left) or the **⚙ gear icon** to open **Connection Settings**.
2. Enter your **Tenant ID** and **Environment Name**.
3. Choose an authentication method:
   - **Basic Auth** — username and password.
   - **OAuth 2.0** — access token URL, client ID, client secret, and client authentication method (`client_secret_post` or `client_secret_basic`).
4. Click **Save**. The connection pill turns green and shows the environment name when connected.

#### Browse & Send Requests

1. The **left panel** lists all API endpoints found in your workspace — pages with `PageType = API` and queries with `QueryType = API`. Use the search bar to filter by name.
2. Click an endpoint to load its URL into the request bar. The `company` query parameter is automatically injected if a company name is available.
3. Select an HTTP **method** (`GET`, `POST`, `PUT`, `PATCH`, `DELETE`) and adjust the URL if needed.
4. Use the **Params** accordion to manage query parameters:
   - Check or uncheck rows to include or exclude individual parameters.
   - The URL bar stays in sync with the params table at all times.
   - The `company` parameter is highlighted with a special accent pill.
5. Click **▶ Send** (or press `Ctrl+Enter`) to fire the request.

#### Inspect the Response

The response area shows:
- **Status code** and status text (colour-coded: green for 2xx, amber for 3xx, red for errors).
- **Response time** (colour-coded by speed: green < 500 ms, amber < 2 s, red ≥ 2 s).
- **Response size** in bytes, KB, or MB.
- **Element count** — items in an array, records in a `value` property, or keys in an object.
- **Call counter** — total requests made in the current session.
- A **syntax-highlighted JSON viewer** with colour-coded keys, strings, numbers, booleans, and null values.

#### Search Within the Response

Once a JSON response is loaded, a **search bar** appears above the response body:
- Type to highlight all matching text across the entire JSON.
- A match counter shows the current position (e.g. `3 / 14`).
- Use the **▲ / ▼ navigation buttons** to jump between matches. The active match is scrolled into view automatically.

### Features at a Glance

- **Workspace endpoint discovery** — automatically scans for AL API pages and queries; click **⟳ Rescan** to refresh after code changes.
- **Params ↔ URL sync** — editing either the URL bar or the params table keeps both in sync; no risk of duplicate or malformed query strings.
- **Session persistence** — performance history (up to 30 calls) is preserved for the session.
- **Ctrl+Enter shortcut** — sends the current request without leaving the keyboard.

---

## 5. Translation Assistant

**Command:** `BC HERO: Open Translation Assistant`

A visual XLIFF editor for managing Business Central translation files. View progress across all locales, edit translations inline, validate quality, and save changes — all without leaving VS Code.

![Translation Assistant](images/TranslationAssistant.png)

### How to Use

#### Select a Translation File

1. Open the panel. BC HERO scans your workspace for XLIFF files (`.xlf`) in a `Translations` folder.
2. The **left panel** lists all files found, each showing:
   - A **language flag** and locale code.
   - A **progress bar** and percentage showing how many strings are translated.
   - Counts for translated ✓, missing ✕, and needs-review ⚑ strings.
3. Use the **search bar** and **status filter** to narrow the list (e.g. show only incomplete files).
4. Click a file to load it in the right panel.

#### Edit Translations

1. The right panel shows all translation units in a table with columns for **ID**, **Source** (original English text), and **Target** (the translation).
2. Click any **Target** cell to open an inline editor. Type the translation directly.
3. Use the **state selector** (Translated, Needs Review, Final, etc.) to set the unit's state.
4. Changes are **saved automatically** — on blur (immediately when you leave the cell) and while typing (after a short delay). No Save button is needed.
5. Press `Escape` to discard changes and revert to the previous value.

#### Filter & Navigate

- Use the **search bar** in the toolbar to filter units by source text, target, ID, or notes.
- Use the **status filter** dropdown to show only Translated, Untranslated, or Needs Review units.
- The **unit counter** always shows how many units match the current filter.

#### Batch Operations

- Check individual rows using the checkboxes on the left, or use the **header checkbox** to select/deselect all visible units.
- With units selected, use the **batch bar** at the top to mark all selected units as **Translated** or **Needs Review** in one action.

#### Notes

- Click the **⊟ note icon** on any row to open a flyout showing developer notes and BC HERO notes attached to that translation unit.
- Notes are read-only and help you understand the context of each string.

#### Validation

- Click **⚑ Validate** in the toolbar to run quality checks on the current file.
- Detected issues (missing translations, source-identical targets, placeholder mismatches) appear in a panel at the bottom.
- Click any validation issue to jump directly to the offending unit in the table.

### Features at a Glance

- **Auto-save** — translations are persisted automatically as you type; no manual save step.
- **Progress tracking** — a header progress bar shows the overall completion percentage for the selected file with colour coding (green ≥ 90 %, amber ≥ 50 %, red < 50 %).
- **Open in editor** — click **↗ Open File** to open the raw XLIFF file in VS Code's text editor.
- **Rescan** — click **↺ Rescan** to pick up newly added translation files without reloading the panel.

---

## 6. Schema Viewer

**Command:** `BC HERO: Open Schema Viewer`

Explore Business Central table schemas visually. Browse tables, inspect every field's type and metadata, view keys and indexes, and understand relationships through an interactive force-directed graph.

![Schema Viewer](images/SchemaViewer.png)

### How to Use

#### Browse Tables

1. Open the panel. All tables detected in your workspace (and linked symbol packages) are listed in the **left panel**.
2. Use the **search bar** in the top toolbar to filter by table name or caption.
3. Use the **Type filter** to show only tables of a specific type (Normal, Temporary, CRM, ExternalSQL).
4. Toggle **Show Obsolete** to include or exclude tables marked obsolete.
5. Click any table to open it in the **detail pane**.

#### Inspect Fields

The detail pane opens with a full field table showing:

| Column | Description |
|---|---|
| # | Field ID |
| Field Name | The AL field name (highlighted if search is active) |
| Type | Data type and length (e.g. `Text[50]`, `Decimal`) |
| Caption | The field's display caption |
| Relation | The related table (shown as `→ TableName`) |
| Classification | Data classification (e.g. CustomerContent, SystemMetadata) |
| Flags | `IDX` (indexed), `RO` (read-only), `Obs` (obsolete) |

- Click any **column header** to sort the field table by that column. Click again to reverse.
- Use the **field search bar** to filter fields by name, type, or caption within the selected table.
- Click any **field row** to open the **Metadata Sidebar** with full details: field ID, data type, length, option values, editability, index status, table relation, data classification, and obsolete state.

#### View Keys

Click **⊟ Keys** in the detail header to expand a panel showing all table keys and indexes, including which fields each key covers and whether it is the primary (clustered) key or a unique index.

#### Relationship Graph

The lower half of the right panel shows an interactive **force-directed relationship graph**:
- Each table is a node. Arrows represent `TableRelation` dependencies.
- **Click a node** to highlight it and dim all unrelated tables and edges. Click the same node again or click the background to clear the highlight.
- **Drag nodes** to rearrange the layout. Zoom with the scroll wheel or trackpad.
- Use **Show Fields** to display the first 5 field names inside each node.
- Use **Connected Only** to hide tables with no relationships.
- Use **⊡ Fit** to zoom the graph to fit all visible nodes in the viewport.
- Click **⊟ Details** to collapse the detail pane and give the graph more space.

### Features at a Glance

- **↗ Open** — click the Open button in the detail header to jump directly to the table's `.al` source file.
- **Stats bar** — the top toolbar always shows the total number of tables, fields, and relationships in the current schema.
- **Reset** — clears all filters and search terms and restores the default view.

---

## 7. Dependency Graph

**Command:** `BC HERO: Open Dependency Graph`

A full-workspace, interactive dependency map showing how your AL objects relate to one another. See which pages extend which tables, which codeunits subscribe to which events, and how every object fits into the larger picture.

![Dependency Graph](images/DependencyGraph-1.png)

<br>

![Dependency Graph Ext](images/DependencyGraph-2.png)

### How to Use

1. Open the panel. BC HERO scans the workspace and builds the graph automatically.
2. The graph renders all objects as **colour-coded nodes** grouped by object type, with directed edges representing dependencies.
3. **Click a node** to focus it — its direct connections are highlighted and everything else is dimmed. Click the same node or the background to clear.
4. **Drag nodes** to reorganise the layout. Pan by dragging the background. Zoom with the scroll wheel.
5. **Right-click a node** to open a context menu with options to open the source file, focus connections, or copy the object name or ID.
6. **Hover over a node** to see a tooltip with the object type, ID, file path, and any obsolete or external flags.

### Filtering & Navigation

- **Search bar** — type to dim all nodes that don't match, revealing only matching objects and their immediate neighbours.
- **Type chips** — toggle individual object types (Table, Page, Codeunit, Report, Enum, etc.) on and off to reduce visual clutter. Each type has a distinct colour.
- **Scope toggle** — switch between **Workspace** (your own objects only) and **+ Ext** (includes external/symbol dependencies) to control how much of the graph is shown.

### Relationship Types

Edges are colour-coded by the kind of dependency they represent:

| Colour | Relationship |
|---|---|
| 🟢 Green | SourceTable |
| 🔵 Blue | TableRelation |
| 🟣 Purple | Extends |
| 🟡 Amber | EventSubscriber / EventPublisher |
| ⬦ Default | Other |

### Features at a Glance

- **Node count & edge count** — shown in the stats bar so you always know the current graph size.
- **⊡ Fit** — zooms and pans to fit all visible nodes neatly in the viewport.
- **↺ Reset layout** — re-runs the simulation to generate a fresh automatic layout.
- **Obsolete indicator** — objects marked obsolete display a red dot badge on their node.
- **External dependencies** — objects from symbol packages appear as dimmed, dashed-border nodes so you can distinguish workspace code from platform dependencies.

---

## Getting Started

1. Install **BC HERO** from the Visual Studio Marketplace.
2. Open a Business Central AL workspace in VS Code.
3. Open the **Command Palette** (`Ctrl+Shift+P`) and type `BC HERO` to see all available tools.
4. For API-related features, open **API Explorer** and configure your connection credentials via the **⚙ Connection Settings** dialog before sending requests.

---

## Tips & Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl+Enter` | Send request (API Explorer) / Add object to queue (AL Object Creator) |
| `Escape` | Close modal dialogs / Discard inline translation edit |
| `Ctrl+Shift+P` → `BC HERO` | Open any BC HERO tool from the Command Palette |

- **Rescan buttons** (↺) are available in the API Explorer, Translation Assistant, and AL Object Creator to refresh workspace data without closing and reopening a panel.
- All BC HERO panels share a consistent dark theme, layout, and keyboard patterns — once you learn one, the others feel immediately familiar.
- In the **API Explorer**, the `company` parameter is automatically pinned to the top of the params table and displayed with a distinct accent style so it's never accidentally removed.
- In the **Translation Assistant**, auto-save is silent by default — the VS Code panel only shows a notification for batch operations, not for individual inline edits, keeping your workflow uninterrupted.

---

## Marketplace

BC HERO is available on the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=yahyatouil.bc-hero). Search for **BC HERO** or install directly from the Extensions view in VS Code (`Ctrl+Shift+X`).

---

### **Contributing**

While **pull requests (PRs)** are not currently being accepted, **feedback** is always welcome. If you have ideas for new features or encounter any bugs, feel free to open an **issue** or submit a **feature request**.

To submit feedback:

1. Visit the [GitHub Issues page](https://github.com/yahyatouil-dev/bc-hero-info/issues).
2. Open a new issue with details about the problem or your feature request.

Your input helps improve BC HERO, and we appreciate any contributions you make!

---

### **License Information**

This extension is released under the **Apache License 2.0**. You can freely use, modify, and distribute this software, with some conditions. See the full license text [here](http://www.apache.org/licenses/LICENSE-2.0).

---

### **Feedback & Support**

If you encounter any issues or have questions, don’t hesitate to [open an issue](https://github.com/yahyatouil-dev/bc-hero-info/issues). You can also reach out to the community for support or offer suggestions for new features.

---

### **Stay Updated**

Follow us on GitHub or the **Visual Studio Marketplace** to get the latest updates and announcements about BC HERO. As always, more features are in the pipeline to make your BC development experience even better.


---
## **Powered by Love ❤️**
Made with ❤️ by **Yahya Touil**.

Check out my blog for more insights, tutorials, and updates on Business Central and AL development: [Yahya's Blog](https://yahyatouil.com).

Thank you for supporting **BC HERO** — your feedback and feature requests are always appreciated!
---

*BC HERO — Built for Business Central AL developers.*