# 《舒写》数据模型草案 v1

## 1. Project
```ts
interface Project {
  id: string
  title: string
  genre?: string
  platformTarget?: string[]
  premise?: string
  status: 'idea' | 'outlining' | 'drafting' | 'serializing' | 'archived'
  createdAt: string
  updatedAt: string
}
```

## 2. Idea
```ts
interface Idea {
  id: string
  projectId: string
  rawText: string
  summary?: string
  type?: 'world' | 'character' | 'plot' | 'hook' | 'twist' | 'foreshadow' | 'chapter'
  tags?: string[]
  linkedCharacters?: string[]
  linkedPlotline?: string[]
  expansionSuggestion?: string
  source?: 'text' | 'ocr' | 'voice' | 'manual'
  createdAt: string
}
```

## 3. Outline
```ts
interface Outline {
  id: string
  projectId: string
  premise?: string
  sellingPoints?: string[]
  worldview?: string
  characterMap?: string
  mainPlot?: string
  volumePlan?: string
  pacingNotes?: string
  hookNotes?: string
  updatedAt: string
}
```

## 4. Chapter
```ts
interface Chapter {
  id: string
  projectId: string
  volumeNo?: number
  chapterNo?: number
  title?: string
  goal?: string
  conflict?: string
  hook?: string
  draftText?: string
  polishedText?: string
  status: 'todo' | 'drafting' | 'polishing' | 'reviewing' | 'final' | 'queued' | 'published'
  publishPlanAt?: string
  updatedAt: string
}
```

## 5. Review
```ts
interface Review {
  id: string
  projectId: string
  targetType: 'idea' | 'outline' | 'chapter' | 'character'
  targetId: string
  summary?: string
  strengths?: string[]
  issues?: string[]
  risks?: string[]
  suggestions?: string[]
  score?: number
  createdAt: string
}
```

## 6. SerialPlan
```ts
interface SerialPlan {
  id: string
  projectId: string
  platform: string
  currentPublishedChapter?: number
  draftStock?: number
  publishFrequency?: string
  scheduleNotes?: string
  updatedAt: string
}
```

## 7. 设计原则
- 结构化优先，便于 AI 调用与后续自动化
- 文本字段保留弹性，避免过早过度建模
- 兼容单用户个人工作流，未来可扩多人和多项目
